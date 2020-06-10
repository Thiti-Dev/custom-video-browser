<template>
  <div>
    <SearchBar @termChange="onTermChange" />
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from "./components/SearchBar";

// Importing API_KEY
import {API_KEY} from './config/config.json'

export default {
  name: "App",
  components: { SearchBar },
  methods: {
    async onTermChange(search_str) {
      try {
          const res = await axios.get('https://www.googleapis.com/youtube/v3/search',{
              params:{
                  key: API_KEY,
                  type: 'video',
                  part: 'snippet',
                  q: search_str
              }
          })
          console.log(res)
      } catch (error) {
          console.log(error)
      }
    }
  }
};
</script>