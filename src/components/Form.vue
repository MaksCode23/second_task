<script>
export default {
  name: "Form",
  data(){
    return{
      form:{
        name: '',
        email: '',
      },
      rule:{
        namerule: false,
        nameMsg: '',
        emailrule: false,
        emailMsg: ''
      },
    }
  },
  methods:{
    validateForm(){
      const emailReg = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      this.rule.namerule = this.form.name === '';
      this.rule.nameMsg = "Введіть ім'я"
      this.rule.emailrule = this.form.email === '' || !emailReg.test(this.form.email);
      this.rule.emailMsg =  "Введіть коректну електронну скриньку";

      if (!this.rule.namerule && !this.rule.emailrule) {
        this.submitForm();
      }
    },
    submitForm(){
      alert("Ім'я "+this.form.name + "\nЕлектронна скринька " + this.form.email);
    }
  }
}
</script>

<template>
  <form @submit.prevent="validateForm" novalidate>
    <label for="username">Ім'я</label>
    <input type="text" id="username" v-model="form.name">
    <span v-show="rule.namerule" style="color: red;">{{rule.nameMsg}}</span>
    <br>
    <label for="email">Електронна скринька</label>
    <input type="email" id="email" v-model="form.email">
    <span v-show="rule.emailrule" style="color: red;">{{rule.emailMsg}}</span>
    <v-btn type="submit">Підтвердити</v-btn>
  </form>
</template>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  max-width: 300px;
  margin: 0 auto;
}

label {
  margin-bottom: 8px;
}
input {
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}
button{
  margin-top: 20px;
}
</style>