<script>
import Product from "@/components/Product.vue";

export default {
  name: "NestedList",
  components: {Product},
  data(){
  return{
    Objects:[
      {
        title: "1",
        nestedList:["1.1","1.2","1.3","1.4"]
      },
      {
        title: "2",
        nestedList:["2.1","2.2","2.3","2.4"]
      }
    ]
  }
}
}
</script>

<template>
  <v-container>

    <v-row v-for="(object,i) in Objects" :key="i">
      <v-col cols="12"><h1>{{object.title}}</h1></v-col>
        <v-col v-for="(list,i) in object.nestedList" :key="i">
          <p>{{list}}</p>
        </v-col>
    </v-row>

  </v-container>
</template>

<style scoped>

</style>