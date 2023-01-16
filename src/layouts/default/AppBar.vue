<template>
  <v-app-bar prominent>
    <img src="../../assets/brand-logo.svg" height="34" class="ml-6" />

    <v-spacer></v-spacer>

    <v-text-field
      density="compact"
      variant="outlined"
      label="Search"
      append-inner-icon="mdi-close"
      color="primary"
      hide-details
      single-line
    >
    <template v-slot:prepend-inner>
      <v-icon color="#337AB7">
        mdi-magnify
      </v-icon>
    </template>
    </v-text-field>

    <v-btn size="small" variant="outlined" icon="mdi-filter"></v-btn>

    <v-btn variant="text" icon="mdi-dots-vertical"></v-btn>
  </v-app-bar>
</template>

<script setup>
//
</script>

<style scoped>
/*  */
.v-field__prepend-inner > .v-icon {
  opacity: 1;
}
</style>
