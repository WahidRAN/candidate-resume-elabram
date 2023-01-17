<template>
  <v-card class="table-card">
    <v-dialog v-model="dialog" max-width="500px">
      <template v-slot:activator="{ props }">
        <v-btn color="primary" dark class="mb-2" v-bind="props">
          New Item
        </v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span class="text-h5">{{ formTitle }}</span>
        </v-card-title>

        <v-card-text>
          <v-container>
            <v-row>
              <v-col cols="12" sm="6" md="4">
                <v-text-field
                  v-model="editedItem.avatar"
                  label="Photo"
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="4">
                <v-text-field
                  v-model="editedItem.name"
                  label="Name"
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="4">
                <v-text-field
                  v-model="editedItem.id_number"
                  label="ID Number"
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="4">
                <v-text-field
                  v-model="editedItem.email"
                  label="Email"
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="4">
                <v-text-field
                  v-model="editedItem.register_date"
                  label="Register Date"
                ></v-text-field>
              </v-col>
            </v-row>
          </v-container>
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="blue-darken-1" variant="text" @click="close">
            Cancel
          </v-btn>
          <v-btn color="blue-darken-1" variant="text" @click="save">
            Save
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
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
        <v-icon
          size="small"
          class="action-icon edit"
          @click="editItem(item.raw)"
        >
          mdi-pencil
        </v-icon>
        <v-icon
          size="small"
          class="action-icon delete"
          @click="deleteItem(item.raw)"
        >
          mdi-delete
        </v-icon>
      </template>
    </v-data-table>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      selected: [],
    };
  },
};
</script>

<script setup>
import { ref, computed, nextTick } from "vue";

const itemsPerPage = 5;
const candidateHeaders = [
  {
    title: "No",
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
const candidates = ref([
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
//   {
//     index: 5,
//     avatar: "avatar2",
//     name: "Fulan2",
//     id_number: "123459",
//     email: "fulan2@gmail.com",
//     register_date: new Date().toLocaleDateString(),
//     action: "default2",
//   },
//   {
//     index: 6,
//     avatar: "avatar",
//     name: "Fulan",
//     id_number: "123456",
//     email: "fulan@gmail.com",
//     register_date: new Date().toLocaleDateString(),
//     action: "default",
//   },
//   {
//     index: 7,
//     avatar: "avatar2",
//     name: "Fulan2",
//     id_number: "123459",
//     email: "fulan2@gmail.com",
//     register_date: new Date().toLocaleDateString(),
//     action: "default2",
//   },
//   {
//     index: 8,
//     avatar: "avatar",
//     name: "Fulan",
//     id_number: "123456",
//     email: "fulan3@gmail.com",
//     register_date: new Date().toLocaleDateString(),
//     action: "default",
//   },
//   {
//     index: 9,
//     avatar: "avatar",
//     name: "Fulan",
//     id_number: "123456",
//     email: "fulan@gmail.com",
//     register_date: new Date().toLocaleDateString(),
//     action: "default",
//   },
//   {
//     index: 10,
//     avatar: "avatar2",
//     name: "Fulan2",
//     id_number: "123459",
//     email: "fulan2@gmail.com",
//     register_date: new Date().toLocaleDateString(),
//     action: "default2",
//   },
//   {
//     index: 11,
//     avatar: "avatar",
//     name: "Fulan",
//     id_number: "123456",
//     email: "fulan@gmail.com",
//     register_date: new Date().toLocaleDateString(),
//     action: "default",
//   },
//   {
//     index: 12,
//     avatar: "avatar2",
//     name: "Fulan2",
//     id_number: "123459",
//     email: "fulan2@gmail.com",
//     register_date: new Date().toLocaleDateString(),
//     action: "default2",
//   },
//   {
//     index: 13,
//     avatar: "avatar",
//     name: "Fulan",
//     id_number: "123456",
//     email: "fulan3@gmail.com",
//     register_date: new Date().toLocaleDateString(),
//     action: "default",
//   },
//   {
//     index: 14,
//     avatar: "avatar",
//     name: "Fulan",
//     id_number: "123456",
//     email: "fulan@gmail.com",
//     register_date: new Date().toLocaleDateString(),
//     action: "default",
//   },
//   {
//     index: 15,
//     avatar: "avatar2",
//     name: "Fulan2",
//     id_number: "123459",
//     email: "fulan2@gmail.com",
//     register_date: new Date().toLocaleDateString(),
//     action: "default2",
//   },
]);
const editedIndex = ref(-1);
const editedItem = ref({
  index: -1,
  avatar: "",
  name: "",
  id_number: "",
  email: "",
  register_date: "",
});
const defaultItem = ref({
  index: -1,
  avatar: "",
  name: "",
  id_number: "",
  email: "",
  register_date: "",
});
const formTitle = computed(() => {
  return editedIndex.value === -1 ? "Add Candidate" : "Edit Candidate";
});

const dialog = ref(false);
const editItem = (item) => {
  console.log(item.email);
  editedIndex.value = candidates.value.indexOf(item);
  editedItem.value = Object.assign({}, item);
  dialog.value = true;
};
const close = async () => {
  dialog.value = false;
  await nextTick();
  editedItem.value = Object.assign({}, defaultItem.value);
  editedIndex.value = -1;
};
const save = () => {
  if (editedIndex.value > -1) {
    Object.assign(candidates.value[editedIndex.value], editedItem.value);
  } else {
    editedItem.value.index = candidates.value.length + 1
    candidates.value.push(editedItem.value);
  }
  close();
};

const dialogDelete = ref(false);
const deleteItem = (item) => {
  editedIndex.value = candidates.value.indexOf(item);
  editedItem.value = Object.assign({}, item);
  dialogDelete.value = true;
};
const closeDelete = async () => {
  dialogDelete.value = false;
  await nextTick();
  editedItem.value = Object.assign({}, defaultItem.value);
  editedIndex.value = -1;
};
const deleteItemConfirm = () => {
  candidates.value.splice(editedIndex.value, 1);
  closeDelete();
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
    .action-icon {
      margin-right: 6px;
      border-radius: 4px;
      padding: 12px;
      color: white;
      &.edit {
        background-color: #ffb300;
      }
      &.delete {
        background-color: #ff2442;
      }
    }
  }
}
</style>
