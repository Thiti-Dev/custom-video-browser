<template>
  <ul :class="getClassnameAdjusted">
    <VideoListItem
      @videoSelect="onVideoSelect"
      v-for="video in videos"
      :key="video.etag"
      :video="video"
    />
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem";
export default {
  name: "VideoList",
  components: {
    VideoListItem
  },
  computed: {
    getClassnameAdjusted() {
      if (this.is_any_selected) {
        return `col-md-4`;
      } else {
        return `col-md-12`;
      }
    }
  },
  methods: {
    onVideoSelect(video) {
      this.$emit("videoSelect", video);
    }
  },
  props: {
    videos: Array,
    is_any_selected: Boolean
  }
};
</script>

<style scoped>
</style>