<script setup lang="ts">
const emit = defineEmits(['close'])
</script>

<template>
  <div class="sidebar-panel is-generic">
    <div class="subpanel-header">
      <h3 class="no-mb">MgH Energy</h3>
      <div
        class="panel-close"
        tabindex="0"
        @keydown.space.prevent="emit('close')"
        @click="emit('close')"
      ></div>
    </div>
    <div class="inner" data-simplebar>
      <ul>
        <li>
          <RouterLink to="/liveTraffic">
            <img
              src="/images/icons/icon8/icons8-road-lamps-64.png"
              alt="road-lamps"
              style="width: 36px !important"
            />
            <span
              style="margin-top: 10px !important; position: absolute; margin-left: 10px"
              >Canlı Trafik</span
            >
          </RouterLink>
        </li>
        <li class="mt-3">
          <RouterLink to="/liveCam">
            <img
              src="/images/icons/icon8/icons8-cctv-64.png"
              alt="road-lamps"
              style="width: 36px !important"
            />
            <span
              style="margin-top: 10px !important; position: absolute; margin-left: 10px"
              >Canlı İzle</span
            >
          </RouterLink>
        </li>
        <li class="mt-3">
          <RouterLink to="/incidentDetect">
            <img
              src="/images/icons/icon8/icons8-incident-64.png"
              alt="road-lamps"
              style="width: 36px !important"
            />
            <span
              style="margin-top: 10px !important; position: absolute; margin-left: 10px"
              >Olay Algılama</span
            >
          </RouterLink>
        </li>
        <li class="mt-3">
          <RouterLink to="/plateDetect">
            <img
              src="/images/icons/icon8/icons8-recognition-64.png"
              alt="road-lamps"
              style="width: 36px !important"
            />
            <span
              style="margin-top: 10px !important; position: absolute; margin-left: 10px"
              >Plaka Tanıma</span
            >
          </RouterLink>
        </li>
        <li class="mt-3">
          <RouterLink to="/plateRegis">
            <img
              src="/images/icons/icon8/icons8-driver-license-80.png"
              alt="road-lamps"
              style="width: 36px !important"
            />
            <span
              style="margin-top: 10px !important; position: absolute; margin-left: 10px"
              >Plaka Kayıt</span
            >
          </RouterLink>
        </li>
        <li class="mt-3">
          <RouterLink to="/plateFind">
            <img
              src="/images/icons/icon8/icons8-automobile-64.png"
              alt="road-lamps"
              style="width: 36px !important"
            />
            <span
              style="margin-top: 10px !important; position: absolute; margin-left: 10px"
              >Plaka Sorgula</span
            >
          </RouterLink>
        </li>
        <li class="mt-3">
          <RouterLink to="/stats">
            <img
              src="/images/icons/icon8/icons8-statistic-64.png"
              alt="road-lamps"
              style="width: 36px !important"
            />
            <span
              style="margin-top: 10px !important; position: absolute; margin-left: 10px"
              >İstatistikler</span
            >
          </RouterLink>
        </li>
      </ul>
    </div>
  </div>
</template>

<style lang="scss">
@import '/@src/scss/layout/sidebar-panel';
</style>
