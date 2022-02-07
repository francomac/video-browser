<template>
  <div class="container">
    <search-bar @search-text="onSearchTextChange" />
    <video-list @onVideoSelect="onVideoSelect" />
    <!-- <video-list :videos-list="videosList" @onVideoSelect="onVideoSelect" /> -->
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
  data() {
    return {
      videosList: [],
    };
  },
  components: {
    SearchBar,
    VideoList,
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
          this.videosList = res.data.items;
        })
        .catch((err) => {
          console.log(err);
          this.videosList = [];
        });
    },
    onVideoSelect($event) {
      console.log($event);
    },
  },
};
</script>

<style></style>
