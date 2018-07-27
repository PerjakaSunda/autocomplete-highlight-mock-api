<template>
  <div class="products">
    <div
      class="product"
      v-for="(p, i) in highlights"
      :key="i"
      @click="goDetail(p.id)"
    >
      <div>
        <highlightText :productName="p.name" :searchQuery="searchQuery"></highlightText>
      </div>
      <div>{{ p.price }}</div>
    </div>
  </div>
</template>

<script>
import HighlightText from './HighlightText'

export default {
  props: [
    'searchQuery',
    'highlights'
  ],
  name: 'product',
  components: {
    HighlightText
  },
  methods: {
    goDetail (pid) {
      this.$router.push({name: 'Detail', query: {id: pid}})
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
