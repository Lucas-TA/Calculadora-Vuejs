<script setup lang="ts">
    import { reactive } from 'vue';

    const state = reactive({
        firstNumber: 0,
        secondNumber: 0,
        signal: 'sum',
    })

    function calculate() {
        // Convert input values to numbers
        const num1:number = state.firstNumber;
        const num2:number = state.secondNumber;

        if (isNaN(num1) || isNaN(num2)) {
            return "Digite os valores nos campos disponíveis";
        }

        switch (state.signal) {
            case 'sum':
                return num1 + num2;
            case 'minus':
                return num1 - num2;
            case 'multiply':
                return num1 * num2;
            case 'divide':
                if (num2 === 0) {
                    return "Não é possível dividir por zero";
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
                @change="(e:any) => {if(e.target) state.firstNumber = parseFloat(e.target.value)}"
                type="number" 
                placeholder="Digite um número"
            >
            <select
                @change="(e:any)=> { if (e.target) state.signal = (e.target as HTMLOptionElement).value }"
                class="btn btn-primary text-center d-flex me-2 ms-2">
                <option value="sum">+</option>
                <option value="minus">-</option>
                <option value="multiply">x</option>
                <option value="divide">&#247;</option>
            </select>
            <input
                @change="(e:any) => {if(e.target) state.secondNumber = parseFloat(e.target.value)}"
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
