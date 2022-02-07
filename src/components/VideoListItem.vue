<template>
  <li class="media list-group-item" @click="onVideoSelect">
    <img src="../assets/img/yt_thumbnail.jpeg" alt="youtube thumbnail" />
    <div class="media-body">
      {{ videoElement.snippet.title }}
    </div>
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: {
    videoElement: {
      type: Object,
      default: () => {
        return {};
      },
      required: true,
    },
  },
  computed: {
    thumbnalUrl() {
      //   return this.videoElement.snippet.thumbnails.default.url;
      return "../assets/img/yt_thumbnail.jpeg";
    },
  },
  methods: {
    onVideoSelect() {
      this.$emit("onVideoSelect", this.videoElement);
    },
  },
};
</script>

<style scoped>
li {
  display: flex;
  cursor: pointer;
}
li:hover {
  background-color: #eee;
}
</style>
