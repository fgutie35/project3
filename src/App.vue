<script setup>
import {ref} from 'vue'

const myArray = ref([])
const name = ref('')
const input_name = ref('')
const input_number = ref('')

const toAdd = () =>{
  if(intput_content.value.trim() === '' || input_number.value.trim() === ''){
    return 
 }

 MyArray.value.push({
  content: input_name.value,
  number: input_number,
  done: false
 })

 input_name.value = ''
 input_number.value = ''

}

</script>


<template>
  <main class="content">
    <h1 class="main-title"> 
      Contact List
    </h1>
    <h2>Input your contact information.</h2> 
    <h3>First name is needed in order to create list</h3>

  <section class="formItems">
    <form @submit.prevent = "toAdd">
        First name: <br />
      <input type="text" placeholder="EnterFirstName" v-model="input_name">
      <br /><br />

      Phone Number: <br />
      <input type="text" placeholder="EnterFirstName" v-model="input_number">
      <br /><br />



    </form>

  </section>





  </main>


</template>


<style scoped>


</style>
