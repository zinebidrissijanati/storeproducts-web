<template>
  <div>
    <v-app-bar app dark>
      <v-toolbar-title class="headline text-uppercase">
        <span>Store</span>
        <span class="font-weight-light">Products</span>
      </v-toolbar-title>
      <v-spacer />
      <span class="mr-2">
        Salmane Idrissi Janati
        <v-menu left bottom>
          <template v-slot:activator="{ on }">
            <v-btn icon v-on="on">
              <v-icon>mdi-dots-vertical</v-icon>
            </v-btn>
          </template>

          <v-list>
            <v-list-item>
              <v-list-item-title>
                <v-icon>mdi-power</v-icon>Sign Out
              </v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
      </span>
    </v-app-bar>
  </div>
</template>

<script>
export default {
  name: "NavBar"
};
</script>