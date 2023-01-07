<script setup lang="ts">
import { useHead } from '@vueuse/head'

import { useViewWrapper } from '/@src/stores/viewWrapper'

const viewWrapper = useViewWrapper()
viewWrapper.setPageTitle('Canlı İzle')

useHead({
  title: 'Canlı İzle',
})
</script>

<template>
  <div class="page-content-inner">
    <h1>Deneme İçerikler</h1>
  </div>
</template>
