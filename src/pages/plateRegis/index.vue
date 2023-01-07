<script setup lang="ts">
import { useHead } from '@vueuse/head'

import { useViewWrapper } from '/@src/stores/viewWrapper'

const viewWrapper = useViewWrapper()
viewWrapper.setPageTitle('Plaka Kayıt')

useHead({
  title: 'Plaka Kayıt',
})
</script>

<template>
  <div class="page-content-inner">
    <div class="columns">
      <div class="column is-6">
        <div class="columns">
          <i class="lnir lnir-flight-search"></i>
        </div>
      </div>
      <div class="column is-6">
        <h3>dmnnc</h3>
      </div>
    </div>
  </div>
</template>
