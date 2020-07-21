
<template>
  <div>
    <template>
      <v-toolbar flat color="white">
        <v-toolbar-title>Products</v-toolbar-title>
        <v-divider class="mx-4" inset vertical />
        <v-row justify="center">
          <v-col md="6">
            <v-text-field v-model="name" label="Filter by name" outlined dense />
          </v-col>
        </v-row>
      </v-toolbar>
    </template>
    <v-row dense>
      <v-col v-for="(item, index) in pagined" :key="index">
        <product :selectedProducts="selectedProducts" :product="item" />
      </v-col>
    </v-row>
    <template>
      <div class="text-center">
        <v-pagination
          v-model="page"
          :length="Math.ceil(filtred.length/itemsPerPage)"
          prev-icon="mdi-menu-left"
          next-icon="mdi-menu-right"
        />
      </div>
    </template>
  </div>
</template>

<script>
import Products from "@/helpers/productsData.js";
import Product from "@/components/Product.vue";
export default {
  name: "Products",
  props: {
    selectedProducts: {
      type: Array,
      required: true
    }
  },
  components: {
    Product
  },
  data: () => ({
    loading: false,
    selection: 1,
    data: [],
    name: "",
    page: 1,
    itemsPerPage: 3
  }),
  beforeMount() {
    this.data = Products;
  },
  computed: {
    filtred() {
      const currentObject = this;
      return this.data.filter(item => item.name.includes(currentObject.name));
    },
    pagined() {
      return this.filtred.slice(
        (this.page - 1) * this.itemsPerPage,
        this.itemsPerPage * (this.page - 1) + this.itemsPerPage
      );
    }
  }
};
</script>