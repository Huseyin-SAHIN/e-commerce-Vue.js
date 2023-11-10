<template>
  <v-container>
    <h3>Öne Çıkanlar</h3>
    <v-row>
      <v-col v-for="data in AllData" :key="data.id">
        <CardOne :title="data.name" :price="data.price" :src="data.image" :flex="12" />
      </v-col>
    </v-row>
  </v-container>

  <v-container>
    <h3>Çok Satan Ürünler</h3>
    <v-row>
      <v-col v-for="data in AllData" :key="data.id">
        <CardOne :title="data.name" :src="data.image" :flex="12" />
      </v-col>
    </v-row>
  </v-container>

  <v-container>
    <h3>Yıldızlı Ürünler</h3>
    <v-row>
      <v-col v-for="data in AllData" :key="data.id">
        <CardOne :title="data.name" :src="data.image" :flex="12" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import CardOne from '@/components/SalesCard.vue';
import AllData from '@/demoData/highlights';

</script>
