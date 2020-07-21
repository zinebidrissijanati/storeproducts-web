<template>
  <div>
    <v-card :loading="loading" class="mx-auto my-12" max-width="300">
      <v-img height="200" :src="product.featuredPhoto"></v-img>

      <v-card-title>{{ product.name }} | {{ product.price }} $</v-card-title>

      <v-card-text>
        <v-row align="center" class="mx-0">
          <v-rating
            :value="Number(product.rate)"
            color="amber"
            dense
            half-increments
            readonly
            size="14"
          ></v-rating>

          <div class="grey--text ml-4">{{ product.rate }} ({{ product.reviewsCount }})</div>
        </v-row>
      </v-card-text>

      <v-card-actions>
        <v-btn text @click="showModal">More Photos</v-btn>
        <v-btn color="deep-purple" text @click="addProductToCart">Add to cart</v-btn>

        <v-spacer></v-spacer>

        <v-btn icon @click="show = !show">
          <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
        </v-btn>
      </v-card-actions>
      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>

          <v-card-text>{{ product.description }}</v-card-text>
        </div>
      </v-expand-transition>
    </v-card>
    <v-row justify="center">
      <v-dialog v-model="dialog" dark max-width="600">
        <v-card>
          <v-container fluid>
            <v-row>
              <v-col
                v-for="(photo, index) in product.photos"
                :key="index"
                class="d-flex child-flex"
                cols="4"
              >
                <v-card flat tile class="d-flex">
                  <v-img :src="photo" :lazy-src="photo" aspect-ratio="1" class="grey lighten-2">
                    <template v-slot:placeholder>
                      <v-row class="fill-height ma-0" align="center" justify="center">
                        <v-progress-circular indeterminate color="grey lighten-5"></v-progress-circular>
                      </v-row>
                    </template>
                  </v-img>
                </v-card>
              </v-col>
            </v-row>
          </v-container>
          <v-card-actions>
            <v-spacer />

            <v-btn color="blue darken-1" text @click="dialog = false">Exit</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "Product",
  props: {
    product: {
      type: Object,
      required: true
    },
    selectedProducts: {
      type: Array,
      required: true
    }
  },
  data: () => ({
    loading: false,
    selection: 1,
    show: false,
    dialog: false
  }),

  methods: {
    addProductToCart() {
      this.selectedProducts.push(this.product);
    },
    showModal() {
      this.dialog = true;
    }
  }
};
</script>