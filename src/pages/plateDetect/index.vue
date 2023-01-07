<script setup lang="ts">
import { useHead } from '@vueuse/head'

import { useViewWrapper } from '/@src/stores/viewWrapper'

const viewWrapper = useViewWrapper()
viewWrapper.setPageTitle('Plaka Tanıma')

useHead({
  title: 'Plaka Tanıma',
})
</script>

<template>
  <div class="page-content-inner">
    <h1>Plaka Tanıma</h1>
  </div>
</template>
