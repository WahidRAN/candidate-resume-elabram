<template>
  <v-app>
    <v-layout>
      <v-navigation-drawer expand-on-hover rail>
        <v-list nav>
          <v-list-item prepend-icon="mdi-menu" title="Menu"></v-list-item>
        </v-list>

        <v-list density="compact" nav>
          <v-list-item
            prepend-icon="mdi-folder"
            title="My Files"
            value="myfiles"
          ></v-list-item>
          <v-list-item
            prepend-icon="mdi-account-multiple"
            title="Shared with me"
            value="shared"
          ></v-list-item>
          <v-list-item
            prepend-icon="mdi-star"
            title="Starred"
            value="starred"
          ></v-list-item>
        </v-list>
      </v-navigation-drawer>

      <default-bar />
      <default-view />
    </v-layout>
  </v-app>
</template>

<script setup>
import DefaultBar from "./AppBar.vue";
import DefaultView from "./View.vue";
</script>
