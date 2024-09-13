<script setup>
import {ref, onMounted, watch} from 'vue'

const myArray = ref([])
const input_name = ref('')
const input_number = ref('')



const data = () =>{
  if(input_name.value.trim() === '' || input_number.value.trim() === ''){
    return 
 }

 myArray.value.push({
  name: input_name.value,
 })

 input_name.value = ''
 input_number.value = ''

}



onMounted( () => {
 myArray.value = JSON.parse(localStorage.getItem('myArray'))
 || []
 })

watch(input_name, (newVal) => {
  localStorage.setItem('input_name', newVal)
})

watch(myArray, (newVal) => {
    localStorage.setItem('myArray', JSON.stringify(newVal))
  }, {deep: true})

</script>


<template>
  <main class="content">
    <h1 class="main-title"> 
      Contact List
    </h1>
    <h2>Input your contact information.</h2> 
    <h3>First name is needed in order to create list</h3>

  <section class="formItems">
    <form @submit.prevent = "data">
      First name: <br />
      <input type="text" placeholder="EnterFirstName" v-model="input_name"/>
      <br /><br />

      Phone Number: <br />
      <input type="text" placeholder="EnterPhone" v-model="input_number"/>
      <br /><br />

      <input type="submit" value="Submit"/>

    </form>

  </section>

  <section class = "toAdd">
    <div class="addNames">
      <h2>Added Contacts: <br /></h2>
      <li v-for="x in myArray" :key="x"> 
          <input type="text" v-model="x.name"/>

      </li>

    </div>

  </section>

  </main>

</template>