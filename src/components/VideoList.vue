<template>
  <ul>
    VideoList
    {{ videos.length }}
    <VideoListItem v-for="video in videos" :key="video.etag" :video="video" />
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem";
export default {
  name: "VideoList",
  components: {
    VideoListItem
  },
  props: {
    videos: Array
  }
};
</script>

<style scoped>
</style>