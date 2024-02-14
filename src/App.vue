<script setup lang="ts">
    import { reactive } from 'vue';
    import Header from './components/Header.vue';
    import MainSection from './components/MainSection.vue';

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
    <Header />
    <MainSection 
        :firstNumber="(e:any) => {if(e.target) state.firstNumber = parseFloat(e.target.value)}"
        :secondNumber="(e:any) => {if(e.target) state.secondNumber = parseFloat(e.target.value)}"
        :signal="(e:any)=> { if (e.target) state.signal = (e.target as HTMLOptionElement).value }"
        :calculate="calculate"
    />
    
</template>

<style scoped>
    input {
        height: 30px;
    }
    select {
        font-size: 18px;
    }
</style>
