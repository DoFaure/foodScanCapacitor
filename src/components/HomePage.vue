<template>
  <div class="container">
  <img src="../../public/assets/logo.gif"/>
    <button class="button is-info" v-on:click="lauchScan">Scanner un produit</button>
  </div>
</template>

<script>
export default {
  name: 'HomePage',
  props: {
    msg: String
  },
  methods: {
    lauchScan() {
      this.$router.push({
        name: "Scan"
      });
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

