<template>
    <h1>Videos</h1>
    <ul>
        <span>{{videosList.length}} videos</span>
        <li v-for="item in videosList" :key="item.id">
            {{ item.etag }}
        </li>
    </ul>
</template>

<script>
export default {
    name: 'VideoList',
  props: {
    videosList: {
      type: Array,
      default: () => {
          return [];
      },
      required: true
    },
  },
}
</script>

<style></style>
