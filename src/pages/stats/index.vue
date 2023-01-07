<script setup lang="ts">
import { useHead } from '@vueuse/head'

import { useViewWrapper } from '/@src/stores/viewWrapper'

const viewWrapper = useViewWrapper()
viewWrapper.setPageTitle('İstatistikler')

useHead({
  title: 'İstatistikler',
})
</script>

<template>
  <div class="page-content-inner">
    <h1>İstatistikler</h1>
  </div>
</template>
