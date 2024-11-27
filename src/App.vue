<template>
  <Navbar />
  <div class="container">
    <div class="row mt-2">
      <div class="col-3">
        <h4 :class="counter > 0 ? 'text-success' : 'text-danger'">Contador: {{ counter }}</h4>
        <button class="btn btn-primary" @click="handledIncrement">+1</button>
        <button class="btn btn-primary m-2" @click="handledreset">Reset</button>
        <button class="btn btn-primary" @click="handleddecrement">-1</button>
       
        <div class="mt-3">
          <button class="btn btn-primary" @click="add" :disabled="addedNumbers.includes(counter)">
            Agregar
          </button>
        </div>
      </div>
      
      <div class="col">
        <h5 class="mt-3">Números Agregados:</h5>
        <ul>
          <li v-for="(number, index) in addedNumbers" :key="index">{{ number }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const counter = ref(0);

const addedNumbers = ref([]);

const handledIncrement = () => {
  counter.value = counter.value + 1;
};

const handledreset = () => {
  counter.value = 0;
};

const handleddecrement = () => {
  counter.value = counter.value - 1;
};

const add = () => {
  if (!addedNumbers.value.includes(counter.value)) {
    addedNumbers.value.push(counter.value); 
  }
};

import Navbar from './components/Navbar.vue';
</script>
