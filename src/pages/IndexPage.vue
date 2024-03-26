<template>
  <q-page
    class="row items-start justify-start q-px-lg q-py-lg"
    :style="'max-width:100%;'"
  >
    <div class="row q-col-gutter-lg">
      <div
        v-for="(thumbnail, index) in thumbnailList"
        :key="index"
        class="col-12 col-sm-4 col-md-3"
      >
        <VideoThumbnail
          :thumbnail_url="thumbnail.thumbnail_url"
          :avatar_url="thumbnail.avatar_url"
          :title="thumbnail.title"
          :author="thumbnail.author"
          :views="thumbnail.views"
        />
      </div>
    </div>
  </q-page>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import VideoThumbnail, {
  ThumbnailProps,
} from 'src/components/VideoThumbnail.vue';

defineOptions({
  name: 'IndexPage',
});

const thumbnailList = ref<ThumbnailProps[]>([
  {
    thumbnail_url: 'https://cdn.quasar.dev/img/parallax1.jpg',
    avatar_url: 'https://cdn.quasar.dev/img/boy-avatar.png',
    title: '아이유와 오지 않는 당신을 기다리며',
    author: '빠더너스 BDNS',
    views: '조회수 94만회 1일 전',
  },
  {
    thumbnail_url: 'https://cdn.quasar.dev/img/parallax2.jpg',
    avatar_url: 'https://cdn.quasar.dev/img/boy-avatar.png',
    title: '아이유와 오지 않는 당신을 기다리며',
    author: '빠더너스 BDNS',
    views: '조회수 94만회 1일 전',
  },
  {
    thumbnail_url: 'https://cdn.quasar.dev/img/mountains.jpg',
    avatar_url: 'https://cdn.quasar.dev/img/boy-avatar.png',
    title: '아이유와 오지 않는 당신을 기다리며',
    author: '빠더너스 BDNS',
    views: '조회수 94만회 1일 전',
  },
  {
    thumbnail_url: 'https://cdn.quasar.dev/img/quasar.jpg',
    avatar_url: 'https://cdn.quasar.dev/img/boy-avatar.png',
    title: '아이유와 오지 않는 당신을 기다리며',
    author: '빠더너스 BDNS',
    views: '조회수 94만회 1일 전',
  },
  {
    thumbnail_url: 'https://cdn.quasar.dev/img/parallax1.jpg',
    avatar_url: 'https://cdn.quasar.dev/img/boy-avatar.png',
    title: '아이유와 오지 않는 당신을 기다리며',
    author: '빠더너스 BDNS',
    views: '조회수 94만회 1일 전',
  },
  {
    thumbnail_url: 'https://cdn.quasar.dev/img/parallax2.jpg',
    avatar_url: 'https://cdn.quasar.dev/img/boy-avatar.png',
    title: '아이유와 오지 않는 당신을 기다리며',
    author: '빠더너스 BDNS',
    views: '조회수 94만회 1일 전',
  },
  {
    thumbnail_url: 'https://cdn.quasar.dev/img/mountains.jpg',
    avatar_url: 'https://cdn.quasar.dev/img/boy-avatar.png',
    title: '아이유와 오지 않는 당신을 기다리며',
    author: '빠더너스 BDNS',
    views: '조회수 94만회 1일 전',
  },
  {
    thumbnail_url: 'https://cdn.quasar.dev/img/quasar.jpg',
    avatar_url: 'https://cdn.quasar.dev/img/boy-avatar.png',
    title: '아이유와 오지 않는 당신을 기다리며',
    author: '빠더너스 BDNS',
    views: '조회수 94만회 1일 전',
  },
]);
</script>

<style lang="scss">
.IP {
  &__container {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    place-content: start;
    place-items: start;
    width: 100%;
    gap: 1rem;
  }
}
</style>
