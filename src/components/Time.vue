<script>
export default {
  name: "Time",
  data(){
    return{
      time:[],
    }
  },
  methods:{
    timeArray(){
      const currentTime = new Date().toLocaleTimeString();
      this.time.push(currentTime)
    },
  },
  computed:{
    reverseArray(){
      return [...this.time].reverse()
    }
  }
}
</script>
<template>
  <v-container>
  <v-btn @click="timeArray">Час кліку</v-btn>
  <v-container>
    <v-row v-for="time in reverseArray">
      <v-col>
        <h1>{{time}}</h1>
      </v-col>
    </v-row>
  </v-container>
  </v-container>
</template>

<style scoped>
</style>