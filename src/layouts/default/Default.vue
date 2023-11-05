<template>
  <v-app>
    <default-bar class="navbar" />

    <default-view />
  </v-app>
</template>

<script setup>
  import DefaultBar from './AppBar.vue'
  import DefaultView from './View.vue'
</script>


<style>
.navbar {
  position: fixed;
  z-index: 1;
  width: 56px;
}
.navbar:hover {
  width: 256px;
  transition: 0.3s;
}
</style>