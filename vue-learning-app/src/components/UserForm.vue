<template>
  <div class="form">
    <h2>Register</h2>

    <label>
      Name:
      <input type="text" v-model="name" />
    </label>

    <label>
      Email:
      <input type="email" v-model="email" />
    </label>

    <label>
      Select gender:
      <select name="" id="" v-model="gender" >
        <option value="">Select Gender</option>
        <option value="male">Male</option>
        <option value="female">Female</option>
      </select>
    </label>

    <label>
      Accept Terms:
      <input type="checkbox" v-model="accepted" />
    </label>

    <button @click="submit">Submit</button>

    <div class="error" v-if="errorMessage">{{ errorMessage }}</div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const name = ref('')
const email = ref('')
const accepted = ref(false)
const errorMessage = ref('')
const gender = ref('')
const successMessage = ref('')

function submit() {
  if(!name.value){
    errorMessage.value = "Name is required."
  }
  if(!email.value){
    errorMessage.value = "Email is required."
  }
  if(!accepted.value){
    errorMessage.value = "T&C Check is required."
  }
  if(!gender.value){
    errorMessage.value = "Gender is required."
  }

  errorMessage.value = ''
  alert(`Submitted!\nName: ${name.value}\nEmail: ${email.value}\nGender: ${gender.value}`)
}
</script>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  width: 300px;
  margin: auto;
}

input[type="text"],
input[type="email"] {
  width: 100%;
  padding: 6px;
}

.error {
  color: red;
  font-weight: bold;
}
</style>
