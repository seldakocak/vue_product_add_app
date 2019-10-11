<template>
  <div class="container">
    <!-- Product Add Form -->
    <h1 class="text-center">Ürün Ekleme Uygulaması</h1>
    <hr />
    <app-add-product></app-add-product>

    <!-- Progress Bar -->
    <app-progress></app-progress>

    <!-- Product List -->
    <h3 class="text-center">Ürün Listesi</h3>
    <hr />
    <app-product-list></app-product-list>
  </div>
</template>

<script>
import AddProduct from "./Components/AddProduct";
import ProductList from "./Components/ProductList";
import Progress from "./Components/Progress";

export default {
  components: {
    appAddProduct: AddProduct,
    appProductList: ProductList,
    appProgress: Progress
  }
};
</script>

<style>
body {
  padding-top: 20px;
  padding-bottom: 20px;
}

.card {
  margin: 15px;
  background-color: #e9ecef;
}

.product-container .card {
  margin: 15px 0px;
  padding: 0px;
  min-height: 300px;
}

.card-title {
  font-size: 1rem;
  margin-top: 10px;
}

.progress {
  margin: 50px 15px;
}

.progress-bar {
  color: #21252a;
}
</style>

