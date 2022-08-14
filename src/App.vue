<template>
<div id="wrapper">
<form @submit.prevent="submit" >
  <my-input name="Username"
  :rules="{required:true,min:5}"
  :value="username.value"
  :error="username.error"
    @update="update"
    placeholder="Type your username"></my-input>
      <my-input name="Password"
  :rules="{required:true,min:10}"
  :value="password.value"
  :error="password.error"
  type="password"
    @update="update"
    placeholder="Type your password"></my-input>
  <my-button background="darkslateblue" color="white" :disabled="!valid" />
</form>
</div>
</template>

<script>
import MyButton from '../MyButton.vue';
import MyInput from '../MyInput.vue';
export default {

components: {
  MyButton,
  MyInput
},
data() {
  return {
   
    username : {
      value: '',
      error : ''
    },
    password : {
      value: '',
      error : ''
  }
}
},
computed: {
  valid() {return !this.username.error && !this.password.error}
},
methods : {
  update({name , value, error}) {
    this[name].value = value,
    this[name].error = error
  },
  submit() {
    console.log('Event')
  }
}

}
</script>

<style scoped>
#wrapper {
  display: flex;
  justify-content: center;
  width: 100%;
}
</style>