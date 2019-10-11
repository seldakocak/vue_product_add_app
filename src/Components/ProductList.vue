<template>
  <div v-if="productList.length > 0">
    <div class="row product-container">
      <app-product-detail v-for="product in productList" :key="product">
        <div class="card">
          <div class="card-body">
            <img class="card-img-top" :src="product.selectedImage" :alt="product.productName" />
            <h5 class="card-title">Ürün Adı</h5>
            <small>
              <strong>Adet :</strong>
              {{ product.productCount }}
            </small>
            <br />
            <small>
              <strong>Fiyat :</strong>
              {{ product.productPrice }}
            </small>
            <br />
            <small>
              <strong>Tutar :</strong>
              {{ product.totalPrice }}
            </small>
          </div>
        </div>
      </app-product-detail>
    </div>
  </div>
</template>
<script>
import { eventBus } from "../main";
import ProductDetail from "./ProductDetail";

export default {
  components: {
    appProductDetail: ProductDetail
  },
  data() {
    return {
      productList: []
    };
  },
  created() {
    eventBus.$on("productAdded", product => {
      if (this.productList.length < 2) {
        this.productList.push(product);
        eventBus.$emit("progressBarUpdated", this.productList.length);
      } else {
        alert("Daha fazla ürün ekleyemezsiniz!");
      }
    });
  }
};
</script>
<style>
</style>