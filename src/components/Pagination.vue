<script>
import axiosInstance from "../../services/axios.js";
import Product from "@/components/Product.vue";
import product from "@/components/Product.vue";
export default {
  name: "Pagination",
  data(){
    return{
      products: [],
      page: 1,
      paginatedElements: 2,
    }
  },
  components:{
  Product,
  },
  methods: {
    getProducts() {
      axiosInstance.get('/products')
          .then(response => {
            this.products = response.data;
          })
          .catch(error => {
            console.log(error)
          })
    },
  },
  computed:{
    pages(){
      return Math.ceil(this.products.length / this.paginatedElements)
    },
    paginatedProducts(){
      if(this.pages < this.page){
        this.page = this.pages
      }
      return this.products.slice(
          (this.page - 1) * this.paginatedElements,
          (this.page - 1) * this.paginatedElements + this.paginatedElements)
    }
  },
  mounted() {
    this.getProducts()
  }
}
</script>

<template>
<v-container>
  <label>Кількість продуктів на 1 сторінці: {{paginatedElements}}</label>
  <v-slider step="1"
            show-ticks="always"
            tick-size="1"
            v-model="paginatedElements"
            :max="products.length"
            min="1"
  ></v-slider>
  <v-pagination
      v-model="page"
      :length="pages"
      rounded="circle"
  ></v-pagination>
  <v-row>
    <v-col v-for="product in paginatedProducts" :key="product.id">
      <Product :product="product"/>
    </v-col>
  </v-row>
</v-container>
</template>

<style scoped>

</style>