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
                <p class="title is-6">Nutriscore : {{ product.nutriscore_grade }}</p>
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
</style>