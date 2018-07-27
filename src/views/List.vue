<template>
  <div>
    <search v-model="searchQuery"></search>
    <product :highlights="highlights" :searchQuery="searchQuery"></product>
  </div>
</template>

<script>
import Product from '../components/Product'
import Search from '../components/Search'
import { request } from '../utils'

export default {
  name: 'list',

  components: {
    Product,
    Search
  },
  data () {
    return {
      searchQuery: '',
      results: [],
      highlights: []
    }
  },
  created () {
    const $ = this
    request(`/api/products`)
      .then(res => {
        if (res.success) {
          $.results = res.data
        }
      })
  },
  watch: {
    'searchQuery': function (v) {
      const $ = this
      const regex = new RegExp(v, 'gi')
      $.highlights = $.results.filter(res => res.name.match(regex))
    },
    'results': function (res) {
      const $ = this
      $.highlights = $.results
    }
  }
}
</script>

<style>

</style>
