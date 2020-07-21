<template>
  <div>
    <Layout>
      <div>
        <router-view :selectedProducts="selectedProducts"/>
      </div>
    </Layout>
  </div>
</template>

<script>
import Layout from '@/layout/Layout.vue';
export default {
  name: 'Home',
  components: {
    Layout,
  },
  data: () => ({
    selectedProducts: [],
    }),
};
</script>