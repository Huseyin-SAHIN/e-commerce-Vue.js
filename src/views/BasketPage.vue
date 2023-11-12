<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <v-list>
          <v-list-item-group v-for="product in cartItems" :key="product.id">
            <v-list-item>
              <v-list-item-avatar>
                <img :src="product.image" alt="Product Image" />
              </v-list-item-avatar>
              <v-list-item-content style="flex: 1">
                <v-list-item-title>
                  {{ product.name }}
                </v-list-item-title>
                <v-list-item-subtitle>
                  {{ product.quantity }} adet - Toplam:
                  {{ product.price * product.quantity }} TL
                </v-list-item-subtitle>
              </v-list-item-content>

              <div style="padding: 10px; display: flex; gap: 1rem">
                <v-list-item-action>
                  <v-btn
                    icon
                    @click="decreaseQuantity(product)"
                    v-if="product.quantity > 1"
                  >
                    <v-icon>mdi-minus</v-icon>
                  </v-btn>
                  <v-btn icon @click="removeItem(product)" v-else>
                    <v-icon>mdi-delete</v-icon>
                  </v-btn>
                </v-list-item-action>
                <v-list-item-action>
                  <v-btn icon>
                    <v-icon>mdi-heart</v-icon>
                  </v-btn>
                </v-list-item-action>
                <v-list-item-action>
                  <v-btn icon @click="increaseQuantity(product)">
                    <v-icon>mdi-plus</v-icon>
                  </v-btn>
                </v-list-item-action>
              </div>
            </v-list-item>
          </v-list-item-group>
          <div v-if="cartItems.length === 0">
            <v-alert type="info" outlined>
              Sepetinizde ürün bulunmamaktadır.
            </v-alert>
          </div>
        </v-list>
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="12">
        <v-divider></v-divider>
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="12" class="text-right">
        Toplam Fiyat: {{ calculateTotalPrice() }} TL
      </v-col>
    </v-row>
  </v-container>
</template>
  
<script setup>
import { ref } from "vue";

const cartItems = ref([
  {
    id: 1,
    name: "Ürün 1",
    image: "https://vera.com.tr/wp-content/uploads/2019/11/urun-resmi-yok.png",
    price: 50,
    quantity: 2,
  },
  {
    id: 2,
    name: "Ürün 2",
    image: "https://vera.com.tr/wp-content/uploads/2019/11/urun-resmi-yok.png",
    price: 30,
    quantity: 1,
  },
]);

const decreaseQuantity = (product) => {
  product.quantity--;
};

const increaseQuantity = (product) => {
  product.quantity++;
};

const removeItem = (product) => {
  const index = cartItems.value.indexOf(product);
  if (index !== -1) {
    cartItems.value.splice(index, 1);
  }
};

const calculateTotalPrice = () => {
  return cartItems.value.reduce((total, product) => {
    return total + product.price * product.quantity;
  }, 0);
};
</script>

  

<style>
v-list-item-avatar {
  width: 100px;
  height: 100px;
}
v-list-item-avatar img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>