<script>
import axiosInstance from "../../services/axios.js";
import product from "@/components/Product.vue";
export default {
  name: "Products",
  components:{

  },
  data(){
    return{
    products:[],
    styles:[],
    }
  },
  methods:{
    getProducts(){
      axiosInstance.get('/products')
          .then(response => {
            this.products = response.data;
            this.randStyles()
          })
          .catch(error=>{
            console.log(error)
          })
    },
    genStyles(){
      const red = Math.floor(Math.random() * 256);
      const green = Math.floor(Math.random() * 256);
      const blue = Math.floor(Math.random() * 256);
      const size = Math.floor(Math.random()*35)+10;
      return {
          colorRGB: `rgb(${red}, ${green}, ${blue})`,
          fontSize: size + 'px',
      }
    },
    randStyles(){
      for(let i = 0; i < this.products.length; i++){
        this.styles.push(this.genStyles())
      }
    },
    changeStyles(i) {
      this.styles[i].fontSize = null
      this.styles[i].colorRGB = null
    },
  },
  created() {
    this.getProducts()
  },

}
</script>

<template>
  <h3>Клік по картці = стандартний розмір шрифту та колір</h3>
  <v-container>
    <v-row>
      <v-col v-for="(product,i) in products" :key="product.id">
        <v-card
            class="mx-auto my-8"
            elevation="24"
            max-width="300"
            min-width="200"
            :style="{background: styles[i].colorRGB , 'border-radius': true }"
                @click="changeStyles(i)"
        >
          <v-card-item>
            <v-card-title :style="{'font-size': styles[i].fontSize}">
              {{product.title}}
            </v-card-title>
            <v-card-subtitle :style="{'font-size': styles[i].fontSize}">
              {{product.description}}
            </v-card-subtitle>
          </v-card-item>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped>

</style>