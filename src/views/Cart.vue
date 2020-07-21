
<template>
  <div>
    <v-data-table
      :headers="headers"
      :items="selectedProducts"
      :items-per-page="5"
      :search="search"
      class="elevation-1"
    >
      <template v-slot:top>
        <v-toolbar flat color="white">
          <v-toolbar-title>The list of selected products</v-toolbar-title>
          <v-divider class="mx-4" inset vertical />
          <v-row>
            <v-col md="6">
              <v-text-field
                v-model="search"
                class="ml-12"
                append-icon="mdi-magnify"
                label="Filter by name"
                single-line
                hide-details
              />
            </v-col>
          </v-row>
        </v-toolbar>
      </template>
      <template v-slot:item.featuredPhoto="{ item }">
        <v-list-item-avatar>
          <v-img class="elevation-6" :src="item.featuredPhoto" />
        </v-list-item-avatar>
      </template>
      <template v-slot:item.price="{ item }">
        <v-chip color="orange" dark>{{ item.price }} $</v-chip>
      </template>
      <template v-slot:item.action="{ item }">
        <v-icon small @click="deleteProduct(selectedProducts.indexOf(item))">mdi-delete</v-icon>
      </template>
      <template v-slot:no-data>no products selected</template>
    </v-data-table>
  </div>
</template>

<script>
export default {
  name: "Cart",
  props: {
    selectedProducts: {
      type: Array,
      required: true
    }
  },
  data: () => ({
    search: "",
    headers: [
      {
        text: "Product",
        align: "left",
        sortable: false,
        value: "featuredPhoto"
      },
      {
        text: "Name",
        align: "left",
        sortable: false,
        value: "name"
      },
      {
        text: "Price",
        align: "left",
        sortable: false,
        value: "price"
      },
      { text: "Actions", value: "action", sortable: false }
    ]
  }),
  methods: {
    deleteProduct(item) {
      this.selectedProducts.splice(item, 1);
    }
  }
};
</script>