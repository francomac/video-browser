<template>
  <div>
    <search-bar @search-text="onSearchTextChange" />
    <video-list :videos-list="videosList" />
  </div>
</template>

<script>
import axios from "axios";
import { YOUTUBE_API } from "./constants";

import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";

const _YOUTUBE_API = YOUTUBE_API;
export default {
    name: "App",
  data () {
    return {
        videosList: {},
    }
  },
  components: {
    SearchBar,
    VideoList
  },
  methods: {
    onSearchTextChange(data) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: _YOUTUBE_API,
            type: "video",
            part: "snippet",
            q: data,
          },
        })
        .then((res) => {
          console.log(res);
          this.videosList = res
        });
    },
  },
};
</script>

<style></style>
