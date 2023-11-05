<template>
  <v-card>
    <v-layout>
      <v-navigation-drawer expand-on-hover rail>
        <v-list>
          <v-list-item prepend-avatar="https://randomuser.me/api/portraits/women/85.jpg" title="Sandra Adams"
            subtitle="sandraadams@gmail.com"></v-list-item>
        </v-list>

        <v-divider></v-divider>

        <v-list density="compact" nav>
          <v-list-item prepend-icon="mdi-home" title="Anasayfa" value="home" />
          <v-list-item prepend-icon="mdi-basket" title="Sepetim" value="basket" />
          <v-list-item prepend-icon="mdi-account" title="Profil" value="profil" />
          <v-list-item prepend-icon="mdi-star" title="Favoriler" value="star" />
          <v-list-item prepend-icon="mdi-cog" title="Ayarlar" value="settings" />
        </v-list>
      </v-navigation-drawer>

      <v-main style="height: 100vh"></v-main>
    </v-layout>
  </v-card>
</template>
