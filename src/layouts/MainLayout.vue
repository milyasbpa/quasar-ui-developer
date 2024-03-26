<template>
  <q-layout view="hHh lpR fFf">
    <q-header
      elevated
      :class="`${
        $q.dark.isActive ? 'bg-dark' : 'bg-white'
      } g-py-xs items-center`"
      :style="'height:56px;'"
    >
      <q-toolbar>
        <div
          :class="'row-auto items-center content-center justify-start justify-items-start'"
          :style="'gap:10px;'"
        >
          <q-btn flat dense round aria-label="Menu" @click="toggleLeftDrawer">
            <q-icon
              :name="matMenu"
              :color="$q.dark.isActive ? 'white' : 'dark'"
              :size="'24px'"
            />
          </q-btn>
          <q-btn :href="'/'" flat no-caps no-wrap class="q-ml-xs">
            <YoutubeIcon :style="'width:90px; height:20px;'" />
          </q-btn>
        </div>

        <button @click="changeTheme">change Theme</button>

        <q-space />

        <AutocompleteSearch />

        <q-space />

        <RightHeader />
      </q-toolbar>
    </q-header>

    <q-drawer show-if-above :mini="!leftDrawerOpen" bordered>
      <q-scroll-area class="fit">
        <q-list padding>
          <q-item v-for="link in links1" :key="link.text" v-ripple clickable>
            <q-item-section avatar :class="'justify-center'">
              <q-icon color="grey" :name="link.icon" />
              <span v-if="!leftDrawerOpen">{{ link.text }}</span>
            </q-item-section>
            <q-item-section>
              <q-item-label>{{ link.text }}</q-item-label>
            </q-item-section>
          </q-item>

          <q-separator class="q-my-md" />

          <q-item v-for="link in links2" :key="link.text" v-ripple clickable>
            <q-item-section avatar>
              <q-icon color="grey" :name="link.icon" />
            </q-item-section>
            <q-item-section>
              <q-item-label>{{ link.text }}</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import { ref, watch } from 'vue';
import { matMenu } from '@quasar/extras/material-icons';
import { useQuasar } from 'quasar';
import YoutubeIcon from 'src/layouts/YoutubeIcon.vue';
import AutocompleteSearch from 'src/layouts/AutocompleteSearch.vue';
import RightHeader from 'src/layouts/RightHeader.vue';

defineOptions({
  name: 'MainLayout',
});

const $q = useQuasar();

const changeTheme = () => {
  $q.dark.toggle();
};

watch(
  () => $q.dark.isActive,
  (val) => {
    console.log(val ? 'Dark Mode' : 'Light Mode');
  }
);

const links1 = [
  { icon: 'home', text: '홈' },
  { icon: 'whatshot', text: 'Shorts' },
  { icon: 'subscriptions', text: '구독' },
];
const links2 = [
  { icon: 'folder', text: '나' },
  { icon: 'restore', text: '시청 기록' },
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>

<style lang="scss"></style>