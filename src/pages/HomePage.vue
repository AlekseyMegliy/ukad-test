<template>
  <div class="home">
    <Header v-bind:page="page"/>
    <HomeMain />
    <Footer />
   
  </div>
</template>

<script>
import Header from '@/components/HeaderComponent.vue'
import HomeMain from '@/components/HomeMainComponent.vue'
import Footer from '@/components/FooterComponent.vue';


export default {
  components: {Header, HomeMain, Footer},
  data() {
    return {
      page:1
    }
  },
  
}
</script>
