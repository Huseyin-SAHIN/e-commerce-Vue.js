<template>
  <v-app-bar app color="primary">
    <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
    <v-toolbar-title>Title</v-toolbar-title>
  </v-app-bar>

  <v-navigation-drawer app v-model="drawer" permanent>
    <v-list>
      <v-list-item-group>
        <v-list-item>
          <v-list-item-avatar class="avatar">
            <v-img src="https://randomuser.me/api/portraits/women/85.jpg"></v-img>
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title>Sandra Adams</v-list-item-title>
            <v-list-item-subtitle>sandraadams@gmail.com</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>

        <v-divider></v-divider>

        <v-list-item v-for="item in items" :key="item.title" link>
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list-item-group>
    </v-list>
  </v-navigation-drawer>
</template>

<script setup>
import { ref } from 'vue';

const drawer = ref(true);
window.addEventListener('resize', () => {
  if (window.innerWidth < 900) drawer.value = false;
  else drawer.value = true;
});

const items = [
  { title: 'Anasayfa', icon: 'mdi-home' },
  { title: 'Sepetim', icon: 'mdi-basket' },
  { title: 'Profil', icon: 'mdi-account' },
  { title: 'Favoriler', icon: 'mdi-star' },
  { title: 'Ayarlar', icon: 'mdi-cog' },
];
</script>


<style>
.appNavbar {
  position: fixed;
  width: 100%;
  z-index: 999;
  background: transparent !important;
  top: 0;
  left: 0;
}

.v-list-item__content {
  display: flex;
  align-items: center;
}

v-list-item-content {
  margin-left: 10px;
}


.avatar {
  width: 45px;
  height: 45px;
  display: block;
}

.avatar .v-responsive img {
  border-radius: 50%;
  width: 44px;
  height: 44px;
}

.avatar .v-responsive .v-responsive__sizer {
  padding-bottom: 50px !important;
  display: inline-block !important;
}
</style>
