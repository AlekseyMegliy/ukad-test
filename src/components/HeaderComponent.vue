<template>
  <div class="header container-fluid">
    <div class="row header-nav">
      <img  class="col-sm-5 col-md-1 logo" src="../assets/UKAD_logo.svg">
      <div class="col-4 col-md-2 row nav">
        <router-link to="/" v-bind:class="{current:page===1}" class="col-2">Home</router-link>
        <router-link to="/products" v-bind:class="{current:page===2}" class="col-2">Products</router-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props:['page']
}
</script>


<style scoped>

.header{
  background-color: #022B32;  
}
.header .header-nav{
  padding: 25px 20px;
  display: flex;
  vertical-align: middle;
}
.header .logo{
  width: 110px;
  padding: 0;
  color: #FFFFFF;
  margin: auto 0;
}
.header .header-nav .nav{
  margin: auto 0;
  color: white;
  display: flex;
  justify-content: space-around;
  
}
.header .header-nav .nav a{
  margin: auto 15px;
  font-size: 16px;
  line-height: 24px;
  text-decoration: none;
  text-transform: uppercase;
  color: #FFFFFF;
}
.header .header-nav .nav .current{
  text-decoration:underline;
}

</style>
