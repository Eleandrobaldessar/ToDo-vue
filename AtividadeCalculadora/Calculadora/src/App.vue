<script setup>
import { reactive, computed } from 'vue';
import InputField from './components/InputField.vue';
import OperationSelect from './components/OperationSelect.vue';

// Estado reativo da calculadora
const estado = reactive({
  valorA: 0,
  valorB: 0,
  operacao: '+'
});

// Função para calcular o resultado com base na operação selecionada
const calcularResultado = computed(() => {
  switch (estado.operacao) {
    case '+':
      return estado.valorA + estado.valorB;
    case '-':
      return estado.valorA - estado.valorB;
    case '*':
      return estado.valorA * estado.valorB;
    case '/':
      return estado.valorB !== 0 ? estado.valorA / estado.valorB : 'Não pode dividir por zero';
    default:
      return 0;
  }
});

// Função para lidar com a mudança dos inputs e operações
const atualizarValorA = (event) => {
  estado.valorA = Number(event.target.value);
};

const atualizarValorB = (event) => {
  estado.valorB = Number(event.target.value);
};

const atualizarOperacao = (event) => {
  estado.operacao = event.target.value;
};
</script>

<template>
  <div class="container">
    <h1 class="my-4">Calculadora Aritmética</h1>
    <form @submit.prevent>
      <div class="row">
        <div class="col">
          <InputField 
            :value="estado.valorA" 
            @input="atualizarValorA" 
            placeholder="Digite o valor A" 
          />
        </div>
        <div class="col">
          <InputField 
            :value="estado.valorB" 
            @input="atualizarValorB" 
            placeholder="Digite o valor B" 
          />
        </div>
        <div class="col-md-2">
          <OperationSelect 
            :value="estado.operacao" 
            @change="atualizarOperacao" 
          />
        </div>
      </div>
    </form>
    <div class="mt-3">
      <strong>Resultado:</strong> {{ calcularResultado }}
    </div>
  </div>
</template>
