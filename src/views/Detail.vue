<template>
  <div v-if="detail" class="product-view">
    <div class="name"> {{ detail.name }} </div>
    <div class="photo"> <img :src="require('@/assets/iphone-7.jpg')"> </div>
    <div class="price"><span class="button"> {{ detail.price }} </span></div>
  </div>
</template>

<script>
import { request } from '../utils'

export default {
  name: 'detail',
  data () {
    return {
      detail: null
    }
  },
  created () {
    const $ = this
    request(`/api/products/1`)
      .then(res => {
        if (res.success) {
          $.detail = res.data
        }
      })
  }
}
</script>

<style>

</style>
