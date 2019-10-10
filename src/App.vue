<template>
  <div class="container">
    <!-- Product Add Form -->
    <h1 class="text-center">Ürün Ekleme Uygulaması</h1>
    <hr>
    <div class="row justify-content-md-center">
      <!-- Product Info -->
      <div class="col-md-5 card">
        <div class="card-body">
          <div class="form-group">
            <label>Ürün Adı</label>
            <input type="text" class="form-control" placeholder="">
          </div>
          <div class="row">
            <div class="form-group col-md-6">
              <label>Ürün Adeti</label>
              <input type="text" class="form-control" placeholder="">
            </div>
            <div class="form-group col-md-6">
              <label>Ürün Fiyatı</label>
              <input type="text" class="form-control" placeholder="">
            </div>
          </div>
          <button class="btn btn-dark btn-block">Ekle</button>
        </div>
      </div>
      <!-- Product Picture -->
      <div class="col-md-3 card">
        <div class="card-body tex-center d-flex align-items-center flex-column">
          <img width="128" height="128" class="img-responsive text-center mb-3"
              :src="product.selectedImage == null ? '/src/assets/default.png' : product.selectedImage">
          <input ref="file" type="file" style="display: none;" @change="onChange($event)" class="form-control">
          <button class="btn btn-outline-dark btn-sm" type="button" @click="$refs.file.click()">Resim Seç</button>
        </div>
      </div>
    </div>
    <!-- Progress Bar -->
    <div class="row justify-content-md-center">
      <div class="w-100 progress">
        <div class="progress-bar bg-info" role="progressbar" style="width: 0%" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100">
          0/10
        </div>
      </div>
    </div>
    <!-- Product List -->
    <h3 class="text-center">Ürün Listesi</h3>
    <hr>
    <div class="row product-container">
      <div class="col-md-3 col-sm-6">
        <div class="card">
          <div class="card-body">
            <img class="card-img-top" src="/src/assets/default.png" alt="Card image cap">

            <h5 class="card-title">Ürün Adı</h5>
            <small>
              <strong>Adet : </strong> 1
            </small>
            <br>
            <small>
              <strong>Fiyat : </strong> 10
            </small>
            <br>
            <small>
              <strong>Tutar : </strong> 10
            </small>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        imageList: [],
        product : {
            selectedImage: null
        }
      }
    },
    methods: {
      onChange(e) {
        const file = e.target.files[0];
        this.product.selectedImage = URL.createObjectURL(file);
      }
    }
  }
</script>

<style>
  body {
    padding-top: 20px;
    padding-bottom: 20px;
  }

  .card{
    margin: 15px;
    background-color:#e9ecef;
  }

  .product-container .card{
      margin: 15px 0px; 
      padding: 0px;
      min-height: 300px;
  }

  .card-title{
    font-size: 1rem;
    margin-top: 10px;
  }

  .progress{
    margin: 50px 15px;
    padding: 15px;
  }

  .progress-bar{
    color: #21252A;
  }
</style>

