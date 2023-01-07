<script setup lang="ts">
import { useHead } from '@vueuse/head'

import { useViewWrapper } from '/@src/stores/viewWrapper'

const viewWrapper = useViewWrapper()
viewWrapper.setPageTitle('Olay Algılama')

useHead({
  title: 'Olay Algılama',
})
</script>

<template>
  <div class="page-content-inner">
    <h1>Olay Algılama</h1>
  </div>
</template>
