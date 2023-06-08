<script>
import { reactive, computed } from 'vue';


export default {
  setup() {
    const estado = reactive({
      valorA: '',
      valorB: '',
      resultado: '',
      operacao: 'escolha'
    });

    const resultado = computed(() => {
      const { valorA, valorB, operacao } = estado;

      const numA = Number(valorA);
      const numB = Number(valorB);

      switch (operacao) {
        case 'soma':
          return numA + numB;
        case 'multiplicação':
          return numA * numB;
        case 'subtração':
          return numA - numB;
        case 'divisão':
          return numA / numB;
        default:
          return '';
      }
    });

    return {
      estado,
      resultado
    };
  }
}
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-secondary rounded-2">
      <h1 class="text-white text-center">Calculadora</h1>
    </header>
    <form>
      <div class="row">
        <div class="col">
          <input v-model="estado.valorA" type="number" placeholder="Digite o valor aqui...A" class="form-control text-center">
          <div class="mt-4 mb-4 justify-content-center">
            <select v-model="estado.operacao" class="form-control text-center justify-content-center">
              <option value="escolha">Escolha uma operação</option>
              <option value="soma">+</option>
              <option value="multiplicação">*</option>
              <option value="subtração">-</option>
              <option value="divisão">/</option>
            </select>
          </div>
          <input v-model="estado.valorB" type="number" placeholder="Digite o valor aqui...B" class="form-control text-center">
        </div>
      </div>
    </form>

    <h3 v-if="resultado !== ''" class="mt-5 text-end text-success">Resultado = {{ resultado }}</h3>
  </div>
</template>

<style scoped>
</style>
