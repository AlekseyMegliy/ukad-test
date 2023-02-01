<template>
    <div class="home-main-block">
        <div class="home-main container-fluid">
            <h1 class=" head">home page</h1>
            <span class="slider-button-left" v-bind:class="{inviz: !shift}"  v-on:click="left"><img src="../assets/Mask.svg"/></span>
            <div  class="row  product-slider">
                
                <Product class=" col-12 col-lg-4 single-product"
                v-touch:swipe.left="right"  
                v-touch:swipe.bottom="right" 
                v-touch:swipe.right="left"
                v-touch:swipe.top="left"
                v-bind:style="{left: shift +'%'}" 
                v-for="item in dogs"
                v-bind:doggy="item"
                v-bind:key="item.id"
                v-bind:limit="max"
                />
        
            </div>      
            <span class="slider-button-right" v-bind:class="{inviz: right_edge}" v-on:click="right"><img src="../assets/Mask.svg"/></span>
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
                max:8,
                shift: 0,
                right_edge: false,
                width: window.innerWidth
            }
        },
        methods:{
            right(){
                if(this.width >991 && Math.floor(this.max/3) > this.shift/(-100)+1){
                this.shift -=100
                } else if(this.width >991 && Math.floor(this.max/3)===this.shift/(-100)+1 && this.max%3===2){
                    this.shift -=66,6666
                    this.right_edge = true
                    
                } else if(this.width >991 && Math.floor(this.max/3)===this.shift/(-100)+1 && this.max%3===1){
                    this.shift -=33,3333
                    this.right_edge = true
                    
                } else if(this.width <= 991 && this.max>this.shift/(-100)+1){
                    this.shift-=100
                    if(this.max===this.shift/(-100)+1){
                        this.right_edge = true
                    }
                   
                }
            },
            left(){
                if(this.width >991 && this.shift%(-100)===0 && this.shift !=0){
                this.shift +=100
                this.right_edge = false
                
                } else if(this.width >991 &&  this.shift%(-100)!=0 && this.max%3===2){
                    this.shift +=66,6666
                    this.right_edge = false
                    
                }else if(this.width >991 &&  this.shift%(-100)!=0 && this.max%3===1){
                    this.shift +=33,3333
                    this.right_edge = false
                    
                }else if(this.width <= 991 && this.shift!=0){
                    this.shift+=100
                    this.right_edge = false
                   
                }
            }, updateWidth() {
                this.width = window.innerWidth;
                this.shift=0
                this.right_edge = false

            }, 
        },
        mounted(){
            fetch("https://api.thedogapi.com/v1/breeds?limit=10&page=0")
            .then(res => res.json())
            .then(data => this.dogs = data)
        },
        created() {
            window.addEventListener('resize', this.updateWidth);
        },
        
    }
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@700&display=swap');
.home-main-block{
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    
}
.home-main{
    position: relative;
    display: flex;
    flex-grow: 1;
    flex-direction: column;
    justify-content: center;
    
}
.home-main .head{
    text-transform: capitalize;
    font-weight: 700;
    font-size: 36px;
    line-height: 54px;
    color: black;
    margin:0 100px;
}
.home-main .product-slider{
    display: flex;
    position: relative;
    flex-wrap: nowrap;
    overflow: hidden;
    margin:0 80px;
}
.home-main .product-slider .single-product{
    position: relative;
    z-index: 0;
    transition: all 0.5s ease-in;
    padding: 0 20px;
}

.home-main .slider-button-left, .home-main .slider-button-right{
    transition: all 0.1s ease-in 0s;
    display: flex;
    position: absolute;
    background: white;
    border-radius: 50%;
    width: 68px;
    height: 68px;
    content: " ";
    top: 45%;
    cursor: pointer;
    margin-top: 0px;
    z-index: 5;
    opacity: 1;
    justify-content: center;
    vertical-align: middle;
    box-shadow:  black 0px 0px 25px -15px;
    
}
.home-main .slider-button-left img, .home-main .slider-button-right img{
    width:12px;
}

.home-main .slider-button-left{
    transform: rotate(180deg);
    left: 4.5%;
    
}

.home-main .slider-button-right{
    right: 4.5%;
    
}

.home-main .slider-button-left:hover, .home-main .slider-button-right:hover{
    box-shadow:  black 0px 0px 35px -13px;
}
.home-main .slider-button-left:active, .home-main .slider-button-right:active{
    box-shadow:  black 0px 0px 0px 0px;
}
 @media all and (max-width:1300px ){
    .home-main .slider-button-left{
        left: 7%;
    }
    .home-main .slider-button-right{
        right: 7%;
    }
    
}
@media all and (max-width:991px ){
    .home-main .head{
        margin: 0 20px;
    }
    .home-main .product-slider{
        margin: 0;
    }
    .home-main .slider-button-left{
        left: 1%;
    }
    .home-main .slider-button-right{
        right: 1%;
    }
    
}

.home-main .inviz{
    display: none;
}
</style>