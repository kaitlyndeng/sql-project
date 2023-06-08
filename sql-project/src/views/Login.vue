<template>
 
  <div class="login">
    <header> Log In </header>
    <form>
      <label for="email">Email:</label>
      <input type="email" id="email" v-model="email">

      <label for="password">Password:</label>
      <input type="password" id="password" v-model="password">

      <button @click="login"> Log In </button>

      <p>Don't have an account?</p>
      <RouterLink to="/signup">Create an Account</RouterLink>
    </form>
  </div>
</template>

<script setup>
import {ref} from 'vue';
import {supabase} from "../supabase";

async function login() {
const {data, error} = await supabase.auth.signInWithPassword({
email: email.value,
password: password.value
})
if (error){
  console.log(error)
}else{
  console.log(data)
}
}
</script>
<style scoped>

</style>
