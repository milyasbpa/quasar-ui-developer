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
          <q-btn
            flat
            dense
            round
            aria-label="Menu"
            @click="$q.screen.lt.sm ? toggleLeftDrawer() : toggleMiniDrawer()"
          >
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

        <q-space />

        <AutocompleteSearch v-if="!$q.screen.lt.sm" />

        <q-space />

        <RightHeader />
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      :mini="$q.screen.lt.sm ? false : !leftMiniOpen"
      bordered
    >
      <div
        v-if="$q.screen.lt.sm"
        :class="'row-auto items-center content-center justify-start justify-items-start q-px-sm'"
        :style="'gap:10px;'"
      >
        <q-btn
          flat
          dense
          round
          aria-label="Menu"
          @click="$q.screen.lt.sm ? toggleLeftDrawer() : toggleMiniDrawer()"
        >
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
      <q-scroll-area class="fit">
        <q-list padding>
          <q-item v-for="link in links1" :key="link.text" v-ripple clickable>
            <div
              :class="
                $q.screen.lt.sm
                  ? 'ML__drawer-item--open'
                  : leftMiniOpen
                  ? 'ML__drawer-item--open'
                  : 'ML__drawer-item--closed'
              "
            >
              <q-icon
                :color="$q.dark.isActive ? 'white' : 'dark'"
                :size="'24px'"
              >
                <HomeIcon v-if="link.icon === 'home'" />
                <ShortIcon v-if="link.icon === 'short'" />
                <SubscriptionIcon v-if="link.icon === 'subscription'" />
              </q-icon>

              {{ link.text }}
            </div>
          </q-item>

          <q-separator class="q-my-md" />

          <q-item v-for="link in links2" :key="link.text" v-ripple clickable>
            <div
              :class="
                $q.screen.lt.sm
                  ? 'ML__drawer-item--open'
                  : leftMiniOpen
                  ? 'ML__drawer-item--open'
                  : 'ML__drawer-item--closed'
              "
            >
              <q-icon
                :color="$q.dark.isActive ? 'white' : 'dark'"
                :size="'24px'"
              >
                <YouIcon v-if="link.icon === 'you'" />
                <HistoryIcon v-if="link.icon === 'history'" />
              </q-icon>
              {{ link.text }}
            </div>
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
import ShortIcon from 'src/layouts/ShortIcon.vue';
import HomeIcon from 'src/layouts/HomeIcon.vue';
import SubscriptionIcon from 'src/layouts/SubscriptionIcon.vue';
import YouIcon from 'src/layouts/YouIcon.vue';
import HistoryIcon from 'src/layouts/HistoryIcon.vue';

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

watch(
  () => $q.screen.sizes.sm,
  (val) => {
    console.log(val ? 'Mobile' : 'Desktop');
  }
);

const links1 = [
  { icon: 'home', text: '홈' },
  { icon: 'short', text: 'Shorts' },
  { icon: 'subscription', text: '구독' },
];
const links2 = [
  { icon: 'you', text: '나' },
  { icon: 'history', text: '시청 기록' },
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  console.log('ini kepanggil ga');
  leftDrawerOpen.value = !leftDrawerOpen.value;
}

const leftMiniOpen = ref(false);

function toggleMiniDrawer() {
  console.log($q.screen.lt.sm, 'ini kepanggil ga');

  leftMiniOpen.value = !leftMiniOpen.value;
}
</script>

<style lang="scss">
.ML {
  &__drawer-item {
    &--open {
      display: grid;
      grid-auto-flow: column;
      gap: 1rem;
      width: 100%;
      align-items: center;
      align-content: center;
      justify-content: flex-start;
      justify-items: flex-start;
    }
    &--closed {
      display: grid;
      grid-template-columns: 1fr;
      gap: 0.5rem;
      width: 100%;
      align-items: center;
      align-content: center;
      justify-content: center;
      justify-items: center;
    }
  }
}
</style>
