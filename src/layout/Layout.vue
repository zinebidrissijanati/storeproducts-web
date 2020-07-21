<template>
  <div>
    <NavBar />
    <v-navigation-drawer absolute permanent dark>
      <div>
        <v-list-item>
          <v-list-item-avatar>
            <v-img
              src="https://avataaars.io/?avatarStyle=Transparent&topType=ShortHairShortCurly&accessoriesType=Prescription02&hairColor=Black&facialHairType=Blank&clotheType=Hoodie&clotheColor=White&eyeType=Default&eyebrowType=DefaultNatural&mouthType=Default&skinColor=Light"
            />
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title class="title">Store Products</v-list-item-title>
            <v-list-item-subtitle>Salmane Idrissi Janati</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>

        <v-divider />

        <v-list dense nav>
          <v-list-item v-for="item in items" :key="item.title" :to="item.link" link>
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </div>
    </v-navigation-drawer>

    <v-content style="margin-left:220px;">
      <v-container class="pl-12 pt-0">
        <slot />
      </v-container>
    </v-content>
  </div>
</template>

<script>
import NavBar from "./NavBar.vue";
export default {
  name: "Layout",
  components: {
    NavBar
  },
  data() {
    return {
      items: [
        { title: "Products", icon: "mdi-store", link: { name: "Products" } },
        { title: "Cart", icon: "mdi-shopping", link: { name: "Cart" } }
      ]
    };
  }
};
</script>