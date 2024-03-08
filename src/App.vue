<script>
export default {
  name: 'App',
  data(){
    return{
      isDarkTheme: false,
      currentTheme: "dark",
    }
  }

}
</script>

<template>

<v-app class="main" :theme="this.isDarkTheme  ? 'dark' : 'light'" >
  <v-switch style="margin: 10px" v-model="isDarkTheme" :label="this.isDarkTheme  ? 'Світла тема' : 'Темна тема'"></v-switch>
  <Global-Component/>

</v-app>

</template>

<style scoped>
.main{
  min-height: 100vh;
  width: 100%;
  margin: 0;
}
</style>
