<script setup>
import { reactive } from 'vue'

const estado = reactive({
    saida: 0,
    valorDoInput1: '',
    valorDoInput2: '',
    opcaoSelecionada: ''
})

function calcular(num1, num2) {
    if (estado.opcaoSelecionada == 'soma') {
        estado.saida = num1 + num2
    } else if (estado.opcaoSelecionada == 'subtracao') {
        estado.saida = num1 - num2
    } else if (estado.opcaoSelecionada == 'divisao') {
        estado.saida = num1 / num2
    } else if (estado.opcaoSelecionada == 'multiplicacao') {
        estado.saida = num1 * num2
    }
}

</script>

<template>
    <div class="container">
        <h1>Calculadora</h1>
        <input type="number" placeholder="Digite um número" v-model="estado.valorDoInput1">
        <input type="number" placeholder="Digite um número" v-model="estado.valorDoInput2">
        <select v-model="estado.opcaoSelecionada" @change="calcular(estado.valorDoInput1, estado.valorDoInput2)">
            <option value="">Escolha uma operação</option>
            <option value="soma">Soma</option>
            <option value="subtracao">Subtração</option>
            <option value="divisao">Divisão</option>
            <option value="multiplicacao">Multiplicação</option>
        </select>
        <h2>Resultado: {{ estado.saida }}</h2>
    </div>
</template>

<style scoped>
.container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    flex-direction: column;
    background-color: beige;
}

input,
select {
    margin-top: 8px;
    padding: 8px;
    max-width: 200px;
}
</style>
