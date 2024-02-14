<script setup lang="ts">
    const props = defineProps(['firstNumber', 'secondNumber', 'signal', 'calculate']);
</script>

<template>
    <main class="container d-flex flex-column justify-content-center align-items-center">
        <h3 class="text-center">Digite dois números e selecione a operação desejada:</h3>
        <div class="text-center d-flex justify-content-center align-items-center p-5">
            <input
                @change="props.firstNumber"
                type="number" 
                placeholder="Digite um número"
            >
            <select
                @change="props.signal"
                class="btn btn-primary text-center d-flex me-2 ms-2">
                <option value="sum">+</option>
                <option value="minus">-</option>
                <option value="multiply">x</option>
                <option value="divide">&#247;</option>
            </select>
            <input
                @change="props.secondNumber"
                type="number" 
                placeholder="Digite um número"
            >
        </div>
        <span>Resultado: {{ props.calculate() }}</span>
    </main>
</template>