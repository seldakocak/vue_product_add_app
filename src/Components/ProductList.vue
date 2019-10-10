<template>
  <div class="row product-container">
    <app-product-detail v-for="product in productList" :key="product">
      <div class="card">
        <div class="card-body">
          <img class="card-img-top" src="/src/assets/default.png" alt="Card image cap" />
          <h5 class="card-title">Ürün Adı</h5>
          <small>
            <strong>Adet :</strong> 1
          </small>
          <br />
          <small>
            <strong>Fiyat :</strong> 10
          </small>
          <br />
          <small>
            <strong>Tutar :</strong> 10
          </small>
        </div>
      </div>
    </app-product-detail>
  </div>
</template>
<script>
import ProductDetail from "./ProductDetail";

export default {
  components: {
    appProductDetail: ProductDetail
  },
  data() {
    return {
      productList: []
    };
  }
};
</script>
<style>
</style>