<script setup>
import { ref, computed } from 'vue'

const n1 = ref(0);
const n2 = ref(0);
const operador = ref('+')
const camposPreenchidos = computed(() => n1.value !== '' && n2.value !== '')

const resultado = computed(() => {
if (!camposPreenchidos.value) return ''

  if (operador.value === '+') {
    return resultado.value = n1.value + n2.value
  } else if (operador.value === '-') {
    return resultado.value = n1.value - n2.value
  } else if (operador.value === '*'){
    return resultado.value = n1.value * n2.value
  } else if (operador.value === '/'){
    return resultado.value = n2.value !== 0 ? Number(n1.value / n2.value).toFixed(2) : 'Não é possível dividir por zero'
  } else return 0
})


</script>

<template>
  <div class="container">
  <h1>Calculadora Aritmética com <span>VueJS</span></h1>
    <div class="input">
      <input v-model.number="n1" type="number" placeholder="Digite um número" >
      <input v-model.number="n2" type="number" placeholder="Digite um número" >
    </div>
    <div class="select">
      <select v-model="operador">
        <option value="+">Soma (+)</option>
        <option value="-">Subtração (-)</option>
        <option value="*">Multiplicação (*)</option>
        <option value="/">Divisão (/)</option>
      </select><br>
    </div>
    <h2>{{ resultado }}</h2>
  </div>
</template>

<style>
body {
  background-color: #e9e9e9;
  font-family: sans-serif;
}

.container {
  margin: 0 auto;
  max-width: 400px;
  width: 100%;
  padding: 32px;
  border: 15px solid black;
  border-radius: 6px;
  background-color: lightblue;background-image: url(https://images.unsplash.com/photo-1695131020187-d3dcdab5016b?q=80&w=685&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D);
}

.input {
  display: flex;
  justify-content: space-evenly;
}

input {
  border: none;
  border-radius: 10px;
  box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.12);
  padding: 10px;
}

.select {
  text-align: center;
  margin: 20px 20px 120px 20px;
}

h1, h2 {
  text-align: center;
}

h2 {
  font-size: 60px;
}

span {
  color: rgb(53, 190, 145);
}
</style>