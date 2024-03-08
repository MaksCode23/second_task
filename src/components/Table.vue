<script>
import axiosInstance from "../../services/axios.js";
import Product from "@/components/Product.vue";
export default {
  name: "Table",
  components:{
    Product,
  },
  data() {
    return {
      products: [],
      rows: 3,
      cols: 3,
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
  },
  mounted() {
    this.getProducts()
  }
}

</script>

<template>

  <div>
    <label>Кількість рядків: {{rows}}</label>
    <v-slider step="1"
              show-ticks="always"
              tick-size="1"
              v-model="rows"
              max="5"
              min="1"
    ></v-slider>
    <label>Кількість стовпців:{{cols}}</label>
    <v-slider step="1"
              show-ticks="always"
              tick-size="1"
              v-model="cols"
              max="4"
              min="1"
    ></v-slider>
    <v-container>
      <v-row v-for="row in rows" :key="row">
        <v-col v-for="col in cols">
            <Product
                      v-if="products[(row - 1) * cols + col - 1]"
                      :key="products[(row - 1) * cols + col - 1].id"
                      :product="products[(row - 1) * cols + col - 1]"></Product>
        </v-col>
      </v-row>
<!--  <v-row v-for="row in rows" :key="row">
        <v-col v-for="col in cols" :key="col">
          <template v-for="(product, index) in products">
            <Product v-if="index === (row - 1) * cols + col - 1" :product="product"></Product>
          </template>
        </v-col>
      </v-row>-->
    </v-container>
  </div>
</template>

<style scoped>

</style>