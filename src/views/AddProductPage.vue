<template>
    <v-container>
      <v-row justify="center">
        <v-col cols="12">
          <v-card>
            <v-card-title class="headline text-center"
              >Yeni Ürün Ekle</v-card-title
            >
            <v-card-text>
              <v-form @submit.prevent="addProduct">
                <div class="image-preview" @click="openFileInput">
                  <img
                    v-if="productImage"
                    :src="productImage"
                    alt="Product Preview"
                  />
                  <div v-else class="placeholder-text">Ürün Resmi Seç</div>
                </div>
                <input
                  type="file"
                  ref="fileInput"
                  style="display: none"
                  accept="image/*"
                  @change="handleFileChange"
                />
                <v-text-field
                  v-model="productTitle"
                  label="Ürün Başlığı"
                  prepend-icon="mdi-label"
                  class="mt-4"
                ></v-text-field>
                <v-text-field
                  v-model="productPrice"
                  label="Ürün Fiyatı"
                  prepend-icon="mdi-currency-usd"
                  class="mt-4"
                  type="number"
                ></v-text-field>
                <v-btn
                  type="submit"
                  color="primary"
                  class="mt-4"
                  size="large"
                  block
                >
                  Ekle
                </v-btn>
              </v-form>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </template>
    
    <script>
  export default {
    data() {
      return {
        productImage: "",
        productTitle: "",
        productPrice: "",
      };
    },
    methods: {
      addProduct() {
        console.log("Ürün Resmi:", this.productImage);
        console.log("Ürün Başlığı:", this.productTitle);
        console.log("Ürün Fiyatı:", this.productPrice);
        // Burada ürün eklenme işlemlerini gerçekleştirebilirsiniz.
      },
      openFileInput() {
        this.$refs.fileInput.click();
      },
      handleFileChange(event) {
        const file = event.target.files[0];
        if (file) {
          const reader = new FileReader();
          reader.onload = () => {
            this.productImage = reader.result;
          };
          reader.readAsDataURL(file);
        }
      },
    },
  };
  </script>
    
    <style>
  .image-preview {
    position: relative;
    width: 100%;
    height: 25vh;
    border: 2px dashed #ccc;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
  }
  
  .image-preview img {
    max-width: 100%;
    max-height: 100%;
  }
  
  .placeholder-text {
    color: #666;
  }
  </style>
    