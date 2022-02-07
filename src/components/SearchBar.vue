<template>
  <div>
    <input @input="onInput" type="text" />
  </div>
</template>

<script>
export default {
    methods: {
        onInput: function($event) {
            this.$emit('searchText', $event.target.value.trim())
        },
    }
};
</script>

<style></style>
