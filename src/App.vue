<template>
    <div id="app">
      <header>
        <h3>{{sitename}}</h3>
        <button @click="showCheckout">{{this.cart.length}} Checkout</button>
      </header>
      <product-list :products ="products" @addProduct='addToCart'></product-list>
      <checkout :cart="cart" @removeProduct='removeFromCart'></checkout>
    </div>
</template>

<script>
import Checkout from './components/Form.vue'
import productList from './components/Products.vue'

export default {
  
        components: {
            productList,
            Checkout
        },
        name: "App",
        data() {
            return {
              sitename:"Afterschool Application",
                cart: [],
                products: [{
                        subject: "Agric",
                        location: "Latvia",
                        price: 3220,
                        description: "Learn Agriculture with us",
                        image: 'Agric.jpg',
                        inventory: 10,
                        inCart: 0
                    },
                    {
                        subject: "Geography ",
                        location: "Kyiv",
                        price: 6700,
                        description: "Learn About the world with us",
                        image: 'geo.jpg',
                        inventory: 10,
                        inCart: 0
                    },
                    {
                        subject: "Mathematics",
                        location: "China",
                        price: 9010,
                        description: "Learn calculations with us",
                        image: 'math.jpg',
                        inventory: 10,
                        inCart: 0
                    },
                    {
                        subject: "Music",
                        location: "Cotonou",
                        price: 2300,
                        description: "Learn About beautiful sounds with us",
                        image: 'music.jpg',
                        inventory: 10,
                        inCart: 0
                    },
                    {
                        subject: "Arts",
                        location: "Oyo",
                        price: 5000,
                        inventory: 10,
                        inCart: 0
                    },
                    {
                        subject: "Music",
                        location: "Uk",
                        price: 980,
                        inventory: 10,
                        inCart: 0
                    }
                ]
            }
        },
        methods: {
            showCheckout: function(){
                    this.showProduct = this.showProduct ? false : true;
                },
            addToCart(product){
                let added = false;
                this.cart.forEach((product2) => {
                    if(product2.id === product.id){
                         product.inCart++
                         added = true
                    }
                });
                    if(!added){
                        this.cart.push(product)
                        product.inCart = 1
                    }    
                        product.inventory--; 
             
            },
            removeFromCart(product){
                this.cart.forEach((product2) => {
                    if(product2.id === product.id) {
                        product.inventory++;
                        product.inCart--
                    }
                })
            }    
        }
    }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
</style>