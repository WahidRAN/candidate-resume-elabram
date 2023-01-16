<template>
  <section class="main-content">
    <v-card class="filter-card"> Something </v-card>
    <v-card class="table-card">
      <div class="table-card-header">
        <h1>Resume</h1>
        <section class="table-card-tools"></section>
      </div>
      <!-- TODO export sass var to template -->
      <v-data-table
        :items-per-page="itemsPerPage"
        :headers="candidateHeaders"
        :items="candidates"
        v-model="selected"
        item-value="name"
        show-select
        class="elevation-1 table-container"
        density="comfortable"
        height="calc(100vh - 64px - 48px - 36px - 48px - 48px)"
      ></v-data-table>
    </v-card>
  </section>
</template>

<script setup>
const itemsPerPage = 10
const candidateHeaders = [
  {
    title: "no",
    align: "start",
    key: "index",
  },
  {
    title: "photo",
    align: "start",
    sortable: false,
    key: "avatar",
  },
  {
    title: "name",
    align: "start",
    key: "name",
  },
  {
    title: "ID number",
    align: "start",
    key: "id_number",
  },
  {
    title: "email",
    align: "start",
    key: "email",
  },
  {
    title: "register date",
    align: "start",
    key: "register_date",
  },
  {
    title: "action",
    align: "start",
    sortable: false,
    key: "action",
  },
];
const candidates = [
  {
    index: 1,
    avatar: "avatar",
    name: "Fulan",
    id_number: "123456",
    email: "fulan@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default",
  },
  {
    index: 2,
    avatar: "avatar2",
    name: "Fulan2",
    id_number: "123459",
    email: "fulan2@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default2",
  },
  {
    index: 3,
    avatar: "avatar",
    name: "Fulan",
    id_number: "123456",
    email: "fulan3@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default",
  },
  {
    index: 1,
    avatar: "avatar",
    name: "Fulan",
    id_number: "123456",
    email: "fulan@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default",
  },
  {
    index: 2,
    avatar: "avatar2",
    name: "Fulan2",
    id_number: "123459",
    email: "fulan2@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default2",
  },
  {
    index: 1,
    avatar: "avatar",
    name: "Fulan",
    id_number: "123456",
    email: "fulan@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default",
  },
  {
    index: 2,
    avatar: "avatar2",
    name: "Fulan2",
    id_number: "123459",
    email: "fulan2@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default2",
  },
  {
    index: 3,
    avatar: "avatar",
    name: "Fulan",
    id_number: "123456",
    email: "fulan3@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default",
  },
  {
    index: 1,
    avatar: "avatar",
    name: "Fulan",
    id_number: "123456",
    email: "fulan@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default",
  },
  {
    index: 2,
    avatar: "avatar2",
    name: "Fulan2",
    id_number: "123459",
    email: "fulan2@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default2",
  },
  {
    index: 1,
    avatar: "avatar",
    name: "Fulan",
    id_number: "123456",
    email: "fulan@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default",
  },
  {
    index: 2,
    avatar: "avatar2",
    name: "Fulan2",
    id_number: "123459",
    email: "fulan2@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default2",
  },
  {
    index: 3,
    avatar: "avatar",
    name: "Fulan",
    id_number: "123456",
    email: "fulan3@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default",
  },
  {
    index: 1,
    avatar: "avatar",
    name: "Fulan",
    id_number: "123456",
    email: "fulan@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default",
  },
  {
    index: 2,
    avatar: "avatar2",
    name: "Fulan2",
    id_number: "123459",
    email: "fulan2@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default2",
  },
];
</script>

<script>
export default {
  data() {
    return {
      // itemsPerPage: 10,
      selected: [],
    };
  },
};
</script>

<style scoped lang="scss">
.main-content {
  display: flex;
  background-color: #f1f2f7;
  // justify-content: space-between;
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
  .table-card {
    width: calc(100% - 20% - 24px);
    .table-container {
      text-transform: capitalize;
      font-weight: 600;
      color: #1b1b28;
    }
  }
}
</style>
