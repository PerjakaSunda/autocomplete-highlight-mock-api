<template>
  <div class="search-container">
    <input
      class="search"
      type="text"
      v-bind:value="search"
      v-on:input="$emit('input', $event.target.value)"
    >
  </div>
</template>

<script>
export default {
  props: ['search'],
  name: 'search'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
