<template>
  <div>
    <h3>Scanner un produit</h3>
    <StreamBarcodeReader
      @decode="(a, b, c) => onDecode(a, b, c)"
      @loaded="() => onLoaded()"
    ></StreamBarcodeReader>
  </div>
</template>

<script>
import { StreamBarcodeReader } from "vue-barcode-reader";

export default {
  name: "Scan",
  components: {
    StreamBarcodeReader,
  },
  data() {
    return {
      id: null,
    };
  },
  props: {
    msg: String,
  },
  methods: {
    onDecode(a, b, c) {
      if (this.id) clearTimeout(this.id);
      this.$router.push({
        name: "ProductDetail",
        params: { id: a+b+c }
      });
    },
    onLoaded() {
      console.log("load");
    }
  },
};
</script>