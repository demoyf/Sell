<template>
  <div id="app">
    <v-header :seller="seller"></v-header>

  </div>
</template>
<script>
import header from  './components/header/header.vue';
const ERR_NO = 0;
export default {
  name: 'app',
  data () {
    return {
      url: './../seller.json',
      seller: {}
    }
  },
  created () {
    this.$http.get(this.url).then((response) => {
        response = response.body;
        if (response.errno === ERR_NO) {
          this.seller = Object.assign({}, this.seller, response.data);
          console.log(response.data);
        }
    })
  },
  components: {
    'v-header': header
  }
}
</script>
<style>

</style>
