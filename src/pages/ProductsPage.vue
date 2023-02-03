<template>
  <div class="products">
    <Header v-bind:page="page" />
    <ProductsMain />
    <Footer />
  </div>
</template>

<script>
import Header from "@/components/HeaderComponent.vue";
import ProductsMain from "@/components/ProductsMainComponent.vue";
import Footer from "@/components/FooterComponent.vue";

export default {
  components: { Header, ProductsMain, Footer },
  data() {
    return {
      page: 2,
    };
  },
};
</script>

<style>
.products {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}
</style>
