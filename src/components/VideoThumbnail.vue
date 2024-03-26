<template>
  <div :class="'Y__thumbnail-container'">
    <img
      :src="props.thumbnail_url"
      :style="'width:100%; border-radius:1rem;'"
    />

    <div :class="'Y__thumbnail-footer'">
      <QAvatar size="26px" :class="'q-mr-[12px]'">
        <img :src="props.avatar_url" />
      </QAvatar>

      <div :class="'Y__thumbnail-footer-information'">
        <span>{{ props.title }}</span>
        <a
          href=""
          :class="`Y__thumbnail-author${$q.dark.isActive ? '--dark' : ''}`"
          >{{ props.author }}</a
        >
        <span
          :class="`Y__thumbnail-views${$q.dark.isActive ? '--dark' : ''}`"
          >{{ props.views }}</span
        >
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { QAvatar } from 'quasar';
export interface ThumbnailProps {
  thumbnail_url: string;
  avatar_url: string;
  title: string;
  author: string;
  views: string;
}

const props = withDefaults(defineProps<ThumbnailProps>(), {
  thumbnail_url: '',
  avatar_url: '',
  title: '',
  author: '',
  views: '',
});
</script>

<style lang="scss">
.Y {
  &__thumbnail-container {
    display: grid;
    grid-template-columns: 1fr;
    place-content: start;
    place-items: start;
    row-gap: 1rem;
    width: 100%;
  }
  &__thumbnail-footer {
    display: grid;
    grid-auto-flow: column;
    gap: 0.5rem;
    place-content: start;
    place-items: start;
    width: 100%;
  }

  &__thumbnail-footer-information {
    display: grid;
    grid-template-columns: 1fr;
    gap: 0.125rem;
    place-content: start;
    place-items: start;
    width: 100%;
  }

  &__thumbnail-author {
    font-size: 0.75rem;
    text-decoration: none;
    font-weight: 400;
    color: #606060;
    &:hover {
      color: #0f0f0f;
    }
    &--dark {
      color: #aaa;
      &:hover {
        color: #fff;
      }
    }
  }

  &__thumbnail-views {
    font-size: 0.75rem;
    font-weight: 400;
    color: #606060;

    &--dark {
      color: #aaa;
    }
  }
}
</style>
