<template>
  <section class="main-content">
    <v-card class="filter-card"> Something </v-card>
    <DashboardTable></DashboardTable>
  </section>
</template>

<script setup>
import DashboardTable from './DashboardTable.vue'
</script>

<style scoped lang="scss">
.main-content {
  display: flex;
  background-color: #f1f2f7;
  gap: 24px;
  padding: 24px;
  .filter-card,
  .table-card {
    padding: 18px;
    border-radius: 12px;
  }
  .filter-card {
    width: 20%;
  }
}
</style>
