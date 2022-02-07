<template>
  <div v-if="!!videoElement" class="col-md-8">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe
        class="embed-responsive-item"
        :src="thumbnalUrl"
        title="YouTube video player"
      />
    </div>
    <div class="details">
      <h4>
        {{ videoElement.snippet.title }}
      </h4>
      <p>{{ videoElement.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "VueListItemDetail",
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
      return `https://www.youtube.com/embed/${this.videoElement.videoId}`;
    },
  },
};
</script>

<style scoped>
.details {
  margin-top: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
}
</style>
