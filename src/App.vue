<script setup>
import { ref, watch } from 'vue';

const num1 = ref(0);
const num2 = ref(0);
const operacao = ref('soma');
const result = ref(0);

const calcular = () => {
    const n1 = parseFloat(num1.value);
    const n2 = parseFloat(num2.value);

    switch (operacao.value) {
        case 'soma':
            result.value = n1 + n2;
            break;
        case 'subtracao':
            result.value = n1 - n2;
            break;
        case 'multiplicacao':
            result.value = n1 * n2;
            break;
        case 'divisao':
            result.value = n1 / n2;
            break;
        default:
            result.value = 'Invalid operation';
    }
};

watch([num1, num2, operacao], calcular);
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
        <h1>Calculadora Aritmética com Vue.js</h1>
        <p>
            Digite os valores e selecione a operação:
        </p>
    </header>
    <form>
        <div class="row">
            <div class="col-md-2">
                <input v-model="num1" required
                    type="text" placeholder="Número 1" class="form-control">
            </div>
            <div class="col-md-2">
                <input  v-model="num2" required
                    type="text" placeholder="Número 2" class="form-control">
            </div>
            <div class="col-md-2">
                <select v-model="operacao" class="form-control form-select">
                    <option value="soma">Soma</option>
                    <option value="subtracao">Subtração</option>
                    <option value="multiplicacao">Multiplicação</option>
                    <option value="divisao">Divisão</option>
                </select>
            </div>
            <div class="col-md-2">
              <input v-model="result" type="text" placeholder="Resultado" class="form-control" disabled>
            </div>
        </div>
    </form>
  </div>
</template>

<style scoped>

</style>
