<script setup lang="ts">
import { DefaultApolloClient } from '@vue/apollo-composable'
import { apolloClient } from './common/ApolloClient'
import { isDark } from '~/common/composables'

// https://v4.apollo.vuejs.org/
provide(DefaultApolloClient, apolloClient)

// https://github.com/vueuse/head
// you can use this to manipulate the document head in any components,
// they will be rendered correctly in the html results with vite-ssg
useHead({
  title: 'Vitesse Modular NaiveUI',
  meta: [
    { name: 'description', content: 'Opinionated Vite Starter Template' },
    {
      name: 'theme-color',
      content: computed(() => isDark.value ? '#00aba9' : '#ffffff'),
    },
  ],
})
</script>

<template>
  <n-config-provider>
    <n-loading-bar-provider>
      <n-message-provider :to="refMsgTargetEl">
        <n-notification-provider>
          <n-dialog-provider>
            <router-view />
            <div ref="refMsgTargetEl" class="app-msg-target"></div>
          </n-dialog-provider>
        </n-notification-provider>
      </n-message-provider>
    </n-loading-bar-provider>
  </n-config-provider>
</template>
