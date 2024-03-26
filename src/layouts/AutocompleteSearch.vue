<template>
  <div class="YL__toolbar-input-container">
    <div :class="'YL__toolbar-text-input-container'">
      <div class="YL__toolbar-input-box">
        <q-input
          borderless
          dense
          v-model="search"
          placeholder="검색"
          class="col YL__toolbar-input"
        />
      </div>

      <q-btn
        flat
        dense
        round
        class="YL__toolbar-input-search-box"
        :style="
          $q.dark.isActive
            ? 'background:rgba(255,255,255,0.1);'
            : 'background:white;'
        "
      >
        <q-icon
          :name="matSearch"
          :color="$q.dark.isActive ? 'white' : 'dark'"
          :size="'24px'"
        />
        <q-tooltip>Search</q-tooltip>
      </q-btn>
    </div>

    <q-btn :href="'/'" flat no-caps no-wrap class="q-ml-xs">
      <MicIcon :style="'width:24px; height:24px;'" />
      <q-tooltip>Mic</q-tooltip>
    </q-btn>
  </div>
</template>

<script setup lang="ts">
import { ref, watch } from 'vue';

import { matSearch } from '@quasar/extras/material-icons';
import { useQuasar } from 'quasar';
import MicIcon from 'src/layouts/MicIcon.vue';

defineOptions({
  name: 'MainLayout',
});

const $q = useQuasar();

watch(
  () => $q.dark.isActive,
  (val) => {
    console.log(val ? 'Dark Mode' : 'Light Mode');
  }
);

const search = ref('');
</script>

<style lang="scss">
.YL {
  &__toolbar-input-container {
    display: grid;
    grid-auto-flow: column;
    gap: 0.125rem;
    align-items: center;
    align-content: center;
    justify-content: center;
    justify-items: center;
  }
  &__toolbar-text-input-container {
    display: grid;
    grid-auto-flow: column;
  }
  &__toolbar-input-box {
    padding: 0px 4px 0px 16px;
    border-radius: 40px 0px 0px 40px;
    border: 1px solid #ccc;
    width: 500px;
  }
  &__toolbar-input {
    width: 100%;
    border: 0px !important;
    outline: 0px !important;
  }
  &__toolbar-input-search-box {
    width: 64px;
    border-radius: 0px 40px 40px 0px;
    border-right: 1px solid #ccc;
    border-bottom: 1px solid #ccc;
    border-top: 1px solid #ccc;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
</style>
