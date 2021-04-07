  
<template>
  <div>
    <h1 class="title is-1">Fiche produit</h1>
    <Product v-if="!isLoading" :product="product" />
    <p v-else>Chargement en cours...</p>
  </div>
</template>


<script>
import Product from "./Product.vue";
import axios from "axios";

export default {
  name: "ProductDetail",
  props: {
    id: String,
  },
  data() {
    return {
      isLoading: true,
      product: {},
    };
  },
  components: {
    Product,
  },
  mounted() {
    axios
      .get(
        "https://world.openfoodfacts.org/api/v0/product/" + this.$route.params.id + ".json"
      )
      .then((response) => {
        console.log(response.data.product);
        this.product = response.data.product;
        this.isLoading = false;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>
