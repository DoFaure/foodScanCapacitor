<template>
  <div class="container">
    <div>
      <img src="../../public/assets/logo.gif"/>
    </div>
    <div>
      <button class="button is-info is-hidden-desktop" v-on:click="lauchScan">Scanner un produit</button>
    </div>
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

