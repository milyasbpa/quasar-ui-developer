<template>
  <div class="YL__toolbar-input-container">
    <div :class="'YL__toolbar-autocomplete-container'">
      <div :class="'YL__toolbar-text-input-container'">
        <div class="YL__toolbar-input-box">
          <q-input
            borderless
            dense
            v-model="search"
            placeholder="검색"
            class="col YL__toolbar-input"
            @focus="handleFocus"
            @blur="handleBlur"
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

        <div
          v-if="isFocus"
          :class="`YL__toolbar-dropdown-container ${
            $q.dark.isActive ? 'bg-dark' : 'bg-white'
          }`"
        >
          <div
            v-for="(list, index) in lists.filter((item) =>
              item.name.toLowerCase().includes(search.toLowerCase())
            )"
            :key="index"
            :class="'YL__toolbar-dropwdown-item'"
          >
            <q-icon
              :name="matSearch"
              :color="$q.dark.isActive ? 'white' : 'dark'"
              :size="'24px'"
            />
            {{ list.name }}
          </div>
        </div>
      </div>
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
const isFocus = ref(false);

const handleFocus = () => {
  isFocus.value = true;
};

const handleBlur = () => {
  isFocus.value = false;
};

const lists = ref([
  {
    id: '1',
    name: 'Daniel',
  },
  {
    id: '2',
    name: 'Joseph',
  },
  {
    id: '3',
    name: 'Noah',
  },
  {
    id: '4',
    name: 'Richard',
  },
  {
    id: '5',
    name: 'Patrick',
  },
]);
</script>

<style lang="scss">
.YL {
  &__toolbar-autocomplete-container {
    position: relative;
  }
  &__toolbar-dropdown-container {
    position: absolute;
    top: 60px;
    z-index: 10;
    left: 0px;
    right: 0px;
    padding: 1rem;
    border-radius: 1rem;
    display: grid;
    grid-template-columns: 1fr;
    gap: 1rem;
    place-content: start;
    place-items: start;
  }
  &__toolbar-dropdown-item {
    display: grid;
    grid-auto-flow: column;
    align-items: center;
    align-content: center;
    justify-items: flex-start;
    justify-content: flex-start;
  }
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
