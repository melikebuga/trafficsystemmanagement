<script setup lang="ts">
import { useHead } from '@vueuse/head'
import { useViewWrapper } from '/@src/stores/viewWrapper'
const viewWrapper = useViewWrapper()
viewWrapper.setPageTitle('Canlı Trafik')

useHead({
  title: 'Canlı Trafik',
})
</script>

<template>
  <div class="page-content-inner">
    <h1>Canlı Trafik Sayfası</h1>
  </div>
</template>
