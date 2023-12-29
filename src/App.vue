<template>
  <div class="app">
    <h1>O problema de Monty Hall</h1>
    <div class="form">
      <div v-if="!started">
        <label for="portsAmont">Quantas portas? </label>
        <input type="text" id="portsAmont" size="3" v-model.number="portsAmont">
      </div>
      <div v-if="!started">
        <label for="selectedPort">Qual porta é premiada? </label>
        <input type="text" id="selectedPort" size="3" v-model.number="selectedPort">
      </div>
      <button v-if="!started" @click="started = true">Iniciar</button>
      <button v-if="started" @click="started = false">Reiniciar</button>
    </div>
    <div class="doors" v-if="started">
      <div v-for="i in portsAmont" :key="i">
        <DoorHall :hasGift="i === selectedPort" :number="i" />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import DoorHall from './components/DoorHall.vue'

let started = ref(false)
let portsAmont = ref(3)
let selectedPort = ref(null)

</script>

<style>
* {
  box-sizing: border-box;
  font-family: 'Montserrat', sans-serif;
}

body {
  color: #fff;
  background: #8360c3;
  /* fallback for old browsers */
  background: -webkit-linear-gradient(to right, #2ebf91, #8360c3);
  /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(to right, #2ebf91, #8360c3);
  /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
}

.app {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.app h1 {
  border: 1px solid #000;
  background-color: #0004;
  padding: 20px;
  margin-bottom: 60px;
}

.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 40px;
}

.form,
.form input,
.form button {
  margin-bottom: 10px;
  font-size: 2rem;
}

.doors {
  align-self: stretch;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>
