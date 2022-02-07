<template>
  <h1>Videos</h1>
  <span>{{ videosList.length }} videos</span>
  <ul class="list-group">
    <VideoListItem
      v-for="item in videosList"
      :key="item.etag"
      :videoElement="item"
      @onVideoSelect="onVideoSelect"
    >
    </VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem.vue";

export default {
  name: "VideoList",
  props: {
    videosList: {
      type: Array,
      default: () => {
        return [
          {
            id: "1",
            etag: "www1",
            snippet: {
              title: "my video 1",
            },
          },
          {
            id: "2",
            etag: "www2",
            snippet: {
              title: "my video 2",
            },
          },
          {
            id: "3",
            etag: "www3",
            snippet: {
              title: "my video 3",
            },
          },
        ];
      },
      required: true,
    },
  },
  components: {
    VideoListItem,
  },
  methods: {
    onVideoSelect($event) {
      this.$emit("onVideoSelect", $event);
    },
  },
};
</script>

<style></style>
