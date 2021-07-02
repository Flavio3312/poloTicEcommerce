<template>
  <div class="home">
        <section class="hero is-link">
         <div class="hero-body">
              <figure class="image is-128x128">
                <img src="../assets/yag.png">
              </figure>
           <p class="title">
              JAGUARETE
            </p>
            <p class="subtitle">
               Hotel *****
            </p>
          </div>
        </section>
        

      
        <div class="columns is-multiline">
           <div class="column is-12">
              <h2 class="is-size-2 has-text-centered">Habitaciones</h2>
               <figure class="image is-1024x720">
                 <AppSlider :slides="slides" />
              </figure>  
            </div>
        
         
      
          <ProductBox 
            v-for="product in latestProducts"
            v-bind:key="product.id"
            v-bind:product="product" />
        </div>
    
  </div>
</template>
<script>
import axios from 'axios'

import ProductBox from '@/components/ProductBox'
import AppSlider from "@/components/AppSlider.vue";
export default {
  name: 'Home',
  
        
  data() {
    return {
      latestProducts:[],
      slides: [
        {
          image:"https://cf.bstatic.com/xdata/images/hotel/max1280x900/283201900.jpg?k=b69920a494deb19be646f25e54cee09c22f2813b85b57275f8ce6c02cd87b45a&o=&hp=1",
          text: "Disponibles"
        },
        {
          image: "https://i.pinimg.com/originals/5a/0b/69/5a0b697646336bcff6b222e73485c4c2.jpg",
          text: "Reserva"
        },
        {
          image: "https://llaollao.com/resources/img/desayuno-balcon.jpg",
          text: "Ahora"
        }
      ],
    }
    
  },
  components: {
    AppSlider,
    ProductBox
    
  },
  mounted() {
    this.getLatestProducts()

    document.title = 'Home | JAGUARETE'
  },
  methods: {
    async getLatestProducts() {
      this.$store.commit('setIsLoading',true)
      await axios
         .get('/api/v1/latest-products')
         .then(response =>{
           this.latestProducts=response.data
         })
         .catch(error =>{
            console.log(error)
          })
      this.$store.commit('setIsLoading',false)   
    } 
  }
}

</script>


