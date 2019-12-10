<template lang="html">
  <div class="border">
    <h3>{{ title }} ({{ language }})</h3>
    <p>from {{ releaseData }}</p>
  </div>
</template>

<script>

export default {
  name: 'Movie',
  props: {
    id: Number,
    title: String,
    releaseData: String,
    language: String
  }
}
</script>

<style lang="css" scoped>
.border {
  border: 2px solid red;
  margin-bottom: -2px;
  background: rgb(235, 235, 235);
}
</style>
