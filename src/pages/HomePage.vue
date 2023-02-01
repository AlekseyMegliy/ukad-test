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

<style>
html {
    height: -webkit-fill-available;
    
}

body {
    height: 100vh;
    min-height: 100vh;
    min-height: -webkit-fill-available;

}
#app{
    min-height: 100vh;
}
.home{
    min-height: 100vh;
}
</style>