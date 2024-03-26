<template>
  <div :class="'RH__container'">
    <q-btn round flat v-if="$q.screen.sm">
      <q-icon
        :name="mdiDotsVertical"
        :color="$q.dark.isActive ? 'white' : 'dark'"
        :size="'24px'"
      />
    </q-btn>
    <q-btn :class="'RH__login-button'">
      <q-icon :name="mdiAccountCircle" :size="'24px'" />
      {{ '로그인' }}
    </q-btn>

    <q-btn round flat dense @click="changeTheme">
      <q-icon :size="'24px'" :color="$q.dark.isActive ? 'white' : 'dark'">
        <NightIcon />
      </q-icon>
    </q-btn>
  </div>
</template>

<script lang="ts" setup>
import { mdiDotsVertical, mdiAccountCircle } from '@quasar/extras/mdi-v7';
import { useQuasar } from 'quasar';
import NightIcon from 'src/layouts/NightIcon.vue';

const $q = useQuasar();

const changeTheme = () => {
  $q.dark.toggle();
};
</script>

<style lang="scss">
.RH {
  &__container {
    display: grid;
    grid-auto-flow: column;
    align-items: center;
    align-content: center;
    justify-content: flex-end;
    justify-items: flex-end;
    gap: 0.5rem;
  }

  &__login-button {
    display: grid;
    grid-auto-flow: column;
    align-items: center;
    align-content: center;
    justify-items: center;
    justify-content: center;
    gap: 0.25rem;
    color: #065fd4;
    border: 1px solid rgba(0, 0, 0, 0.1);
    border-radius: 1rem;
    background-color: white;
    padding: 0.25rem 0.75rem;
    &:hover {
      border: 1px solid #065fd4;
      background-color: rgba(6, 95, 212, 0.1);
    }
  }
}
</style>
