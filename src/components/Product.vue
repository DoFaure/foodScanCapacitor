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
            </div>
            </div>
        </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Product",
  props: {
    product: {},
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