<script setup lang="ts">
import { useHead } from '@vueuse/head'

import { useViewWrapper } from '/@src/stores/viewWrapper'
const companySize = ref('')
const businessType = ref('')
const productToDemo = ref('')
const date = ref(new Date())

const { y } = useWindowScroll()

const isStuck = computed(() => {
  return y.value > 30
})
const onSubmit = () => {
  console.log('Form submitted!')
}

const viewWrapper = useViewWrapper()
viewWrapper.setPageTitle('Plaka Sorgula')

useHead({
  title: 'Plaka Sorgula',
})
</script>

<template>
  <div class="page-content-inner">
    <form class="form-layout" @submit.prevent="onSubmit">
      <div class="form-outer">
        <div :class="[isStuck && 'is-stuck']" class="form-header stuck-header">
          <div class="  ">
            <div class="header help-text">
             <p class="article-head">Plaka Sorgula</p>
            </div>
            <div class="columns">
              <div class="column is-10">
                <VField>
                  <VControl icon="feather:user">
                    <VInput
                      type="text"
                      placeholder="Aracın Sahibini Bul"
                      autocomplete="text"
                      inputmode="text"
                    />
                  </VControl>
                </VField>
              </div>

              <div class="column is-2">

                  <VButton type="submit" color="primary" raised> Sorgula </VButton>

              </div>
            </div>
          </div>
        </div>
        <div class="form-body">
          <div class="card-body">
            <table class="table mb-0">
              <thead class="table">
                <tr>
                  <th scope="col">Kayıtlı Araç Bilgisi</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td>Plaka</td>
                  <td>-</td>
                </tr>
                <tr>
                  <td>Araç Sahibi</td>
                  <td>-</td>
                </tr>
                <tr>
                  <td>İletişim</td>
                  <td>-</td>
                </tr>
                <tr>
                  <td>Adres</td>
                  <td>-</td>
                </tr>
                <tr>
                  <td>Kayıp / Çalıntı</td>
                  <td>-</td>
                </tr>
                <tr>
                  <td>Model</td>
                  <td>-</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </form>
  </div>
</template>
<style lang="scss">
@import '/@src/scss/abstracts/all';
@import '/@src/scss/components/forms-outer';

.form-layout {
  max-width: 740px;
  margin: 0 auto;
}
.article-head{
  font-family: var(--font-alt);
  font-size: 1.25rem;
  font-weight: 300;
  margin-bottom: 0.75rem;
  color: var(--dark-text);
  line-height: 1.125;
}
</style>
