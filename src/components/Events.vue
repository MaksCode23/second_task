<script>
export default {
  name: "Events",
  data(){
    return{
      msgEvents:'',
      checkbox: false,
    }
  },
  methods:{
    firstEvent(){
      this.msgEvents = "Перша подія"
    },
    secondEvent(){
      this.msgEvents = "Друга подія"
    },
    switchEvent(){
      this.checkbox ? this.secondEvent() : this.firstEvent();
    },
  }
}
</script>

<template>
  <div style="display: grid; justify-content: center;" >
    <v-checkbox label="true" v-model="checkbox"/>
    <v-btn @click="switchEvent" style="width: 100px">Подія</v-btn>
    <p>{{msgEvents}}</p>
  </div>
</template>

<style scoped>
button{
  margin-top: 10px;
}
</style>