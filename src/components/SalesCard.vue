<template>
  <v-row dense>
    <v-col :cols="flex">
      <v-card>
        <v-img :src="src" class="align-end" gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)" height="300px" cover>
          <v-card-title class="text-white" :textContent="price"></v-card-title>
        </v-img>

        <v-card-actions v-if="buttons">
          <v-card-title class="text-black" :textContent="title"></v-card-title>
          <v-spacer></v-spacer>
          <v-btn v-for="button in buttons" :key="button.id" :size="button.size || 'small'"
            :color="button.color || 'surface-variant'" :variant="button.text || 'text'" :icon="button.icon || 'mdi-heart'"
            :price="price || '00.00TL'"></v-btn>
        </v-card-actions>

        <v-card-actions v-else>
          <v-card-title class="text-black" :textContent="title"></v-card-title>
          <v-spacer></v-spacer>
          <v-btn size="small" color="surface-variant" variant="text" icon="mdi-cart"></v-btn>
          <v-btn size="small" color="surface-variant" variant="text" icon="mdi-heart"></v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script setup>

defineProps({
  title: String,
  src: String,
  flex: Number,
  cards: Array,
  price: String,
  buttons: Array,
});


</script>