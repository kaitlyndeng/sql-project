<template>
 
    <div class="signup">
      <header> Sign Up </header>
      <form>
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="email">
  
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password">
  
        <button @click="createAcc"> Create Account</button>
  
        <p>Already have an account?</p>
        <RouterLink to="/login">Log In</RouterLink>
      </form>
    </div>
  </template>
  
  <script setup>
  import {ref} from 'vue';
  import {supabase} from "../supabase";
  
  async function createAcc() {
  const {data, error} = await supabase.auth.signUp({
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