<template>
    <div class="products-main container-fluid">
        <h1 class="head">product page</h1>
   
        <div class="row  product-page">
            <Product class=" col-12 col-md-6 col-lg-3 single-product" 
            v-for="item in dogs"
            v-bind:doggy="item"
            v-bind:key="item.id"
            v-bind:limit="max"
            />


        </div>
    </div>
</template>

<script>
    import Product from './ProductComponent.vue';
    export default{
        components:{Product},
        data() {
            return {
                dogs:[],
                max:20
            }
        },
        mounted(){
            fetch("https://api.thedogapi.com/v1/breeds?limit=10&page=0")
            .then(res => res.json())
            .then(data => this.dogs = data)
        }
    }
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@700&display=swap');
.products-main{
    padding: 40px 10px; 
    overflow: hidden;
    
}
.products-main .head{
    text-transform: capitalize;
    font-weight: 700;
    font-size: 36px;
    line-height: 54px;
    color: black;
    padding-left: 10px;
   
}
.products-main .product-page .single-product{
    margin-bottom: 40px;
    padding: 0 20px;
    
}

</style>