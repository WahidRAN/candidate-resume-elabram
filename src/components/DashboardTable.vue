<template>
  <v-card class="table-card">
    <v-dialog v-model="dialogDelete" max-width="500px">
      <v-card>
        <v-card-title class="text-h5"
          >Are you sure you want to delete this item?</v-card-title
        >
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="blue-darken-1" variant="text" @click="closeDelete"
            >Cancel</v-btn
          >
          <v-btn color="blue-darken-1" variant="text" @click="deleteItemConfirm"
            >OK</v-btn
          >
          <v-spacer></v-spacer>
        </v-card-actions>
      </v-card>
    </v-dialog>
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
      height="calc(100vh - 64px - 48px - 36px - 48px - 48px - 24px)"
    >
      <template v-slot:item.index="{ item }">
        <section class="text-center py-6">
          {{ item.raw.index }}
        </section>
      </template>
      <template v-slot:item.avatar="{ item }">
        <section class="d-flex">
          <img
            src="../assets/avatar.jpg"
            :alt="item"
            height="46"
            width="46"
            class="item-avatar"
          />
        </section>
      </template>
      <template v-slot:item.action="{ item }">
        <v-icon size="small" class="mr-2" @click="editItem(item.raw)">
          mdi-pencil
        </v-icon>
        <v-icon size="small" @click="deleteItem(item.raw)"> mdi-delete </v-icon>
      </template>
    </v-data-table>
  </v-card>
</template>

<script setup>
const itemsPerPage = 10;
const candidateHeaders = [
  {
    title: "No.",
    align: "center",
    sortable: false,
    key: "index",
  },
  {
    title: "Photo",
    align: "start",
    sortable: false,
    key: "avatar",
  },
  {
    title: "Name",
    align: "start",
    key: "name",
  },
  {
    title: "ID Number",
    align: "start",
    key: "id_number",
  },
  {
    title: "Email",
    align: "start",
    key: "email",
  },
  {
    title: "Register Date",
    align: "start",
    key: "register_date",
  },
  {
    title: "Action",
    align: "start",
    sortable: false,
    key: "action",
  },
];
const candidates = [
  {
    index: 1,
    avatar: "https://unsplash.com/photos/ZHvM3XIOHoE",
    name: "Muhammad Farhan Bin Umar",
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
    index: 4,
    avatar: "avatar",
    name: "Fulan",
    id_number: "123456",
    email: "fulan@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default",
  },
  {
    index: 5,
    avatar: "avatar2",
    name: "Fulan2",
    id_number: "123459",
    email: "fulan2@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default2",
  },
  {
    index: 6,
    avatar: "avatar",
    name: "Fulan",
    id_number: "123456",
    email: "fulan@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default",
  },
  {
    index: 7,
    avatar: "avatar2",
    name: "Fulan2",
    id_number: "123459",
    email: "fulan2@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default2",
  },
  {
    index: 8,
    avatar: "avatar",
    name: "Fulan",
    id_number: "123456",
    email: "fulan3@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default",
  },
  {
    index: 9,
    avatar: "avatar",
    name: "Fulan",
    id_number: "123456",
    email: "fulan@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default",
  },
  {
    index: 10,
    avatar: "avatar2",
    name: "Fulan2",
    id_number: "123459",
    email: "fulan2@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default2",
  },
  {
    index: 11,
    avatar: "avatar",
    name: "Fulan",
    id_number: "123456",
    email: "fulan@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default",
  },
  {
    index: 12,
    avatar: "avatar2",
    name: "Fulan2",
    id_number: "123459",
    email: "fulan2@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default2",
  },
  {
    index: 13,
    avatar: "avatar",
    name: "Fulan",
    id_number: "123456",
    email: "fulan3@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default",
  },
  {
    index: 14,
    avatar: "avatar",
    name: "Fulan",
    id_number: "123456",
    email: "fulan@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default",
  },
  {
    index: 15,
    avatar: "avatar2",
    name: "Fulan2",
    id_number: "123459",
    email: "fulan2@gmail.com",
    register_date: new Date().toLocaleDateString(),
    action: "default2",
  },
];

const editItem = (item) => {
  console.log(item.email);
};

const deleteItem = (item) => {
  console.log(item);
};
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
.table-card {
  width: calc(100% - 20% - 24px);
  .table-card-header {
    margin-bottom: 24px;
  }
  .table-container {
    font-weight: normal;
    color: #1b1b28;
    .item-avatar {
      border-radius: 100px;
    }
  }
}
</style>
