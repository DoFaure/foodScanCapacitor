<template>
  <div class="columns is-tablet">
    <div class="column is-half is-offset-one-quarter">
        <div class="card">
        <div class="card-image">
            <figure class="image">
            <img
                :src="product.image_url"
                alt="Placeholder image"
            />
            </figure>
        </div>
        <div class="card-content">
            <div class="media">
                <div class="media-content">
                    <p class="title is-4">{{ product.product_name_fr }}</p>
                    <p class="title is-6">Marque : {{ product.brands }}</p>
                    <div v-if="product.nutriscore_grade === 'a'">
                        <img class="nutri-score" src="../../public/assets/nutri-a.png" />
                    </div>
                    <div v-else-if="product.nutriscore_grade === 'b'">
                        <img class="nutri-score" src="../../public/assets/nutri-a.png" />
                    </div>
                    <div v-else-if="product.nutriscore_grade === 'c'">
                        <img class="nutri-score" src="../../public/assets/nutri-c.png" />
                    </div>
                    <div v-else-if="product.nutriscore_grade === 'd'">
                        <img class="nutri-score" src="../../public/assets/nutri-d.png" />
                    </div>
                    <div v-else>
                        <img class="nutri-score" src="../../public/assets/nutri-e.png" />
                    </div>
                    <div>
                        <button class="button is-info is-hidden-desktop" v-on:click="showConfirm">Ajouter aux favoris</button>
                    </div>
                </div>
            </div>
        </div>
        </div>
    </div>
  </div>
</template>

<script>
import { Plugins } from '@capacitor/core';
const { Storage, Modals } = Plugins;

export default {
  name: "Product",
  props: {
    product: {},
  },
  data() {
    return {
      products: {},
    };
  },
  methods: {
    // Plugin Capacitor Modal
    // Demande de confirmation d'ajout du produit aux favoris
    async showConfirm() {
        let confirmRet = await Modals.confirm({
            title: 'ok',
            message: 'Voulez vous ajouter le produit à vos favoris ?'
        });
        if (confirmRet) this.setObject();
    },
    // Sauvegarde du produit dans le localstorage
    // Fonctionne partiellement, enregistre le produit mais écrase les autres
    async setObject() {
        await Storage.set({
            key: 'products',
            value: JSON.stringify( [{
                id: this.product.code,
                name: this.product.product_name_fr
            }])
        });
    },
    // Permet de récupérer la liste des favoris pour ajouter le produit à la liste
    // Non utilisé car difficulté dans la gestion des listes avec le plugin Storage
    async getObject() {
        const ret = await Storage.get({ key: 'products' });
        this.products = JSON.parse(ret.value);
        return this.products;
    }
  }
};
</script>

<style scoped>
.card-image {
    background-color: #e3e3ea;
}
img {
    max-height: 350px;
    width: auto;
    margin: auto;
}
.nutri-score{
    max-width: 200px;
}
</style>