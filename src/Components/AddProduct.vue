<template>
  <div class="row justify-content-md-center">
    <!-- Product Info -->
    <div class="col-md-5 card">
      <div class="card-body">
        <div class="form-group">
          <label>Ürün Adı</label>
          <input type="text" v-model="product.productName" class="form-control" placeholder />
        </div>
        <div class="row">
          <div class="form-group col-md-6">
            <label>Ürün Adeti</label>
            <input type="text" v-model="product.productCount" class="form-control" placeholder />
          </div>
          <div class="form-group col-md-6">
            <label>Ürün Fiyatı</label>
            <input type="text" v-model="product.productPrice" class="form-control" placeholder />
          </div>
        </div>
        <button class="btn btn-dark btn-block" @click="addProduct">Ekle</button>
      </div>
    </div>
    <!-- Product Picture -->
    <div class="col-md-3 card">
      <div class="card-body tex-center d-flex align-items-center flex-column">
        <img
          width="128"
          height="128"
          class="img-responsive text-center mb-3"
          :src="product.selectedImage == null ? '/src/assets/default.png' : product.selectedImage"
        />
        <input
          ref="file"
          type="file"
          style="display: none;"
          @change="onChange($event)"
          class="form-control"
        />
        <button
          class="btn btn-outline-dark btn-sm"
          type="button"
          @click="$refs.file.click()"
        >Resim Seç</button>
      </div>
    </div>
  </div>
</template>
<script>
import { eventBus } from "../main";

export default {
  data() {
    return {
      product: {
        productName: null,
        productCount: null,
        productPrice: null,
        totalPrice: null,
        selectedImage: null
      }
    };
  },
  methods: {
    onChange(e) {
      const file = e.target.files[0];
      this.product.selectedImage = URL.createObjectURL(file);
    },
    addProduct() {
      this.product.totalPrice = this.product.productPrice * this.product.productCount;
      //   console.log(this.product);
      eventBus.$emit("productAdded", this.product);
      this.product = {
        productName: null,
        productCount: null,
        productPrice: null,
        totalPrice: null,
        selectedImage: null
      };
    }
  }
};
</script>
<style>
</style>