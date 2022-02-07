<template>
  <div class="col-md-4">
    <ul class="list-group">
      <VideoListItem
        v-for="item in videosList"
        :key="item.etag"
        :videoElement="item"
        @onVideoSelect="onVideoSelect"
      >
      </VideoListItem>
    </ul>
  </div>
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
            videoId: "HcfHQlUeYo4",
            etag: "www1",
            snippet: {
              title: "my video 1",
              description:
                "hey there! this is a random video #1 from somewhere.",
            },
          },
          {
            id: "2",
            videoId: "esX7SFtEjHg",
            etag: "www2",
            snippet: {
              title: "my video 2",
              description:
                "hey there! this is a random video #2 from somewhere.",
            },
          },
          {
            id: "3",
            videoId: "5qap5aO4i9A",
            etag: "www3",
            snippet: {
              title: "my video 3",
              description:
                "hey there! this is a random video #3 from somewhere.",
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
