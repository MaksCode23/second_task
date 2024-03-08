<script>
import axiosInstance from "../../services/axios.js";
import Product from "@/components/Product.vue";
export default {
  name: "ObjectList",
  components:{
    Product,
  },
  data() {
    return {
    products: [],
    categories: []
    };
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
    getCategories(){
      axiosInstance.get('products/categories')
          .then(response => {
            this.categories = response.data;
          })
          .catch(error => {
            console.log(error)
          })
    }
  },
  mounted() {
    this.getCategories()
    this.getProducts()
  }
}
</script>

<template>
  <v-container>

  <v-row v-for="(category,i) in categories" :key="i">
    <v-col cols="12"><h1>{{category}}</h1></v-col>
      <v-col v-for="product in products.filter(product => product.category === category)" :key="product.id" >
        <Product :product="product" />
      </v-col>
  </v-row>

  </v-container>
</template>

<style scoped>

</style>