<template>
  <div class="container">
    <SearchBar @termChange="onTermChange" />
    <div class="row">
      <VideoDetail :video="selectedVideo" />
      <VideoList
        :is_any_selected="isAnyVideoSelected"
        @videoSelect="onVideoSelect"
        :videos="videos"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetail";

// Importing API_KEY
import { API_KEY } from "./config/config.json";

export default {
  name: "App",
  components: { SearchBar, VideoList, VideoDetail },
  data() {
    return {
      videos: [],
      selectedVideo: null
    };
  },
  computed: {
    isAnyVideoSelected() {
      return !!this.selectedVideo;
    }
  },
  methods: {
    async onTermChange(search_str) {
      try {
        const res = await axios.get(
          "https://www.googleapis.com/youtube/v3/search",
          {
            params: {
              key: API_KEY,
              type: "video",
              part: "snippet",
              q: search_str
            }
          }
        );
        console.log(res);
        this.videos = res.data.items;
      } catch (error) {
        console.log(error);
      }
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    }
  }
};
</script>