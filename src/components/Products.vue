<template>
  <div class="container">
    <p>Liste des produits</p>
  </div>
</template>

<script>
import { Plugins } from '@capacitor/core';
const { Storage } = Plugins;

export default {
  name: "Products",
  data() {
    return {
      listProducts: {},
    };
  },
  methods: {
    async getObject() {
        const ret = await Storage.get({ key: 'products' });
        const products  = JSON.parse(ret.value);
        this.listProducts = products;
        return products;
    }
  },
  mounted() {

    //Récupération des favoris sauvegardés dans le local storage
    //a l'aide du plugin capacitor storage
    this.getObject().then((result) => {
        this.listProducts = result;
        console.log(result);
    });
    console.log(this.listProducts);
  }
};
</script>