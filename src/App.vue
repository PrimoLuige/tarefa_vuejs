<script setup>
import { ref, computed } from 'vue';

// Refs para os números inseridos e a operação selecionada
const num1 = ref(0);
const num2 = ref(0);
const operation = ref('+');

// Cálculo dinâmico com base nos valores e operação
const result = computed(() => {
  switch (operation.value) {
    case '+':
      return num1.value + num2.value;
    case '-':
      return num1.value - num2.value;
    case '*':
      return num1.value * num2.value;
    case '/':
      return num2.value !== 0 ? num1.value / num2.value : 'Erro (divisão por 0)';
    default:
      return 0;
  }
});
</script>

<template>
  <div>
    <h1>Calculadora Aritmética</h1>
    <form>
      <label>
        Número 1:
        <input type="number" v-model.number="num1" />
      </label>
      <label>
        Número 2:
        <input type="number" v-model.number="num2" />
      </label>
      <label>
        Operação:
        <select v-model="operation">
          <option value="+">Soma (+)</option>
          <option value="-">Subtração (-)</option>
          <option value="*">Multiplicação (*)</option>
          <option value="/">Divisão (/)</option>
        </select>
      </label>
    </form>
    <p>Resultado: {{ result }}</p>
  </div>
</template>

<style scoped>
h1 {
  text-align: center;
}

form {
  display: flex;
  flex-direction: column;
  gap: 10px;
  max-width: 300px;
  margin: 0 auto;
}

label {
  display: flex;
  flex-direction: column;
}

input,
select {
  padding: 5px;
  font-size: 1rem;
}

p {
  text-align: center;
  font-size: 1.2rem;
  font-weight: bold;
}
</style>