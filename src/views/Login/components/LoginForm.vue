<script setup lang="ts">
import { reactive, ref, unref, watch } from 'vue'
import { Form } from '@/components/Form'
import { useI18n } from '@/hooks/web/useI18n'
import { ElButton } from 'element-plus'
// , ElCheckbox, ElLink
import { useIcon } from '@/hooks/web/useIcon'
import { useForm } from '@/hooks/web/useForm'
import { loginApi, getTestRoleApi, getAdminRoleApi } from '@/api/login'
import { useCache } from '@/hooks/web/useCache'
import { useAppStore } from '@/store/modules/app'
import { usePermissionStore } from '@/store/modules/permission'
import { useRouter } from 'vue-router'
import type { RouteLocationNormalizedLoaded, RouteRecordRaw } from 'vue-router'
import { UserType } from '@/api/login/types'
import { useValidator } from '@/hooks/web/useValidator'

const { required } = useValidator()

// const emit = defineEmits(['to-register'])

const appStore = useAppStore()

const permissionStore = usePermissionStore()

const { currentRoute, addRoute, push } = useRouter()

const { wsCache } = useCache()

const { t } = useI18n()

const rules = {
  username: [required()],
  password: [required()]
}

const schema = reactive<FormSchema[]>([
  {
    field: 'title',
    colProps: {
      span: 24
    }
  },
  {
    field: 'username',
    value: 'admin',
    component: 'Input',
    colProps: {
      span: 24
    },
    componentProps: {
      placeholder: t('login.usernamePlaceholder'),
      prefixIcon: useIcon({ icon: 'ep:user', color: '#d8e3e9', size: 18 })
    }
  },
  {
    field: 'password',
    value: 'admin',
    component: 'InputPassword',
    colProps: {
      span: 24
    },
    componentProps: {
      style: {
        width: '100%'
      },
      placeholder: t('login.passwordPlaceholder'),
      prefixIcon: useIcon({ icon: 'ep:lock', color: '#d8e3e9', size: 18 })
    }
  },
  // {
  //   field: 'tool',
  //   colProps: {
  //     span: 24
  //   }
  // },
  {
    field: 'login',
    colProps: {
      span: 24
    }
  }
  // {
  //   field: 'other',
  //   component: 'Divider',
  //   label: t('login.otherLogin'),
  //   componentProps: {
  //     contentPosition: 'center'
  //   }
  // },
  // {
  //   field: 'otherIcon',
  //   colProps: {
  //     span: 24
  //   }
  // }
])

// const iconSize = 30

// const remember = ref(false)

const { register, elFormRef, methods } = useForm()

const loading = ref(false)

// const iconColor = '#999'

const redirect = ref<string>('')

watch(
  () => currentRoute.value,
  (route: RouteLocationNormalizedLoaded) => {
    redirect.value = route?.query?.redirect as string
  },
  {
    immediate: true
  }
)

// 登录
const signIn = async () => {
  const formRef = unref(elFormRef)
  await formRef?.validate(async (isValid) => {
    if (isValid) {
      loading.value = true
      const { getFormData } = methods
      const formData = await getFormData<UserType>()

      try {
        const res = await loginApi(formData)

        if (res) {
          wsCache.set(appStore.getUserInfo, res.data)
          // 是否使用动态路由
          if (appStore.getDynamicRouter) {
            getRole()
          } else {
            await permissionStore.generateRoutes('none').catch(() => {})
            permissionStore.getAddRouters.forEach((route) => {
              addRoute(route as RouteRecordRaw) // 动态添加可访问路由表
            })
            permissionStore.setIsAddRouters(true)
            push({ path: redirect.value || permissionStore.addRouters[0].path })
          }
        }
      } finally {
        loading.value = false
      }
    }
  })
}

// 获取角色信息
const getRole = async () => {
  const { getFormData } = methods
  const formData = await getFormData<UserType>()
  const params = {
    roleName: formData.username
  }
  // admin - 模拟后端过滤菜单
  // test - 模拟前端过滤菜单
  const res =
    formData.username === 'admin' ? await getAdminRoleApi(params) : await getTestRoleApi(params)
  if (res) {
    const { wsCache } = useCache()
    const routers = res.data || []
    wsCache.set('roleRouters', routers)

    formData.username === 'admin'
      ? await permissionStore.generateRoutes('admin', routers).catch(() => {})
      : await permissionStore.generateRoutes('test', routers).catch(() => {})

    permissionStore.getAddRouters.forEach((route) => {
      addRoute(route as RouteRecordRaw) // 动态添加可访问路由表
    })
    permissionStore.setIsAddRouters(true)
    push({ path: redirect.value || permissionStore.addRouters[0].path })
  }
}

// 去注册页面
// const toRegister = () => {
//   emit('to-register')
// }
</script>

<template>
  <Form
    :schema="schema"
    :rules="rules"
    label-position="top"
    hide-required-asterisk
    size="large"
    class="dark:(border-1 border-[var(--el-border-color)] border-solid) login-card"
    @register="register"
  >
    <template #title>
      <div class="text-xl text-center w-[100%] p-30px">{{ t('login.login') }}</div>
    </template>

    <!-- <template #tool>
      <div class="flex justify-between items-center w-[100%]">
        <ElCheckbox v-model="remember" :label="t('login.remember')" size="small" />
        <ElLink type="primary" :underline="false">{{ t('login.forgetPassword') }}</ElLink>
      </div>
    </template> -->

    <template #login>
      <div class="w-[100%] pt-30px pb-30px">
        <ElButton :loading="loading" type="primary" class="w-[100%]" round @click="signIn">
          {{ t('login.login') }}
        </ElButton>
      </div>
      <!-- <div class="w-[100%] mt-15px">
        <ElButton class="w-[100%]" @click="toRegister">
          {{ t('login.register') }}
        </ElButton>
      </div> -->
    </template>

    <!-- <template #otherIcon>
      <div class="flex justify-between w-[100%]">
        <Icon
          icon="ant-design:github-filled"
          :size="iconSize"
          class="cursor-pointer anticon"
          :color="iconColor"
        />
        <Icon
          icon="ant-design:wechat-filled"
          :size="iconSize"
          class="cursor-pointer anticon"
          :color="iconColor"
        />
        <Icon
          icon="ant-design:alipay-circle-filled"
          :size="iconSize"
          :color="iconColor"
          class="cursor-pointer anticon"
        />
        <Icon
          icon="ant-design:weibo-circle-filled"
          :size="iconSize"
          :color="iconColor"
          class="cursor-pointer anticon"
        />
      </div>
    </template> -->
  </Form>
</template>

<style lang="less" scoped>
.login-card {
  :deep(.el-col-24) {
    padding: 5px 35px !important;
  }

  :deep(.el-input__wrapper) {
    box-shadow: 0 0 0 2px #e6edf1;
  }
}

:deep(.anticon) {
  &:hover {
    color: var(--el-color-primary) !important;
  }
}
</style>
