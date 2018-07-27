<template>
  <p v-html="hlResult(productName)"></p>
</template>

<script>
export default {
  props: [
    'productName',
    'searchQuery'
  ],
  name: 'highlightText',
  methods: {

    /* Highlight Result */
    hlResult (str) {
      const $ = this
      const regex = new RegExp($.searchQuery, 'gi')
      return str.replace(regex, function (res) {
        return '<span style="color: #1976d2;">' + res + '</span>'
      })
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  span {
    display:inline-block;
  }

  span.highlight {
    color: #108EE9;
  }
</style>
