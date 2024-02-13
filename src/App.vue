<script setup lang="ts">
    import { ref } from 'vue';
    
    const firstNumber = ref<number | string>(0);
    const secondNumber = ref<number | string>(0);
    const signal = ref<string>('sum');

    function calculate(): number | string {
    const num1 = parseFloat(firstNumber.value.toString());
    const num2 = parseFloat(secondNumber.value.toString());
    
    if (isNaN(num1) || isNaN(num2)) {
        return "Digite os valores nos campos disponíveis";
    }

        switch (signal.value) {
            case 'sum':
                return num1 + num2;
            case 'minus':
                return num1 - num2;
            case 'multiply':
                return num1 * num2;
            case 'divide':
                if (num2 === 0) {
                    return "Cannot divide by zero";
                }
                return num1 / num2;
            default:
                return "Operação inválida";
        }
    }

</script>

<template>
    <header class="container">
        <h1 class="text-center p-5"> Calculadora Aritmética</h1>
    </header>
    <main class="container d-flex flex-column justify-content-center align-items-center">
        <h3 class="text-center">Digite dois números e selecione a operação desejada:</h3>
        <div class="text-center d-flex justify-content-center align-items-center p-5">
            <input
                @input="firstNumber = ($event.target as HTMLInputElement).value"
                type="number" 
                placeholder="Digite um número"
            >
            <select v-model="signal" class="btn btn-primary text-center d-flex me-2 ms-2">
                <option value="sum">+</option>
                <option value="minus">-</option>
                <option value="multiply">x</option>
                <option value="divide">&#247;</option>
            </select>
            <input
                @input="secondNumber = ($event.target as HTMLInputElement).value"
                type="number" 
                placeholder="Digite um número"
            >
        </div>
        <span>Resultado: {{ calculate() }}</span>
    </main>
</template>

<style scoped>
    input {
        height: 30px;
    }
    select {
        font-size: 18px;
    }
</style>
