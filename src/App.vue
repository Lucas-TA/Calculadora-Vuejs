<script setup lang="ts">

    function calculateResult(): number | string {
        const firstNumber: number = parseFloat(this.firstNumberInput.toString());
        const secondNumber: number = parseFloat(this.secondNumberInput.toString());

        switch (this.selectedOperation) {
            case 'sum':
                return firstNumber + secondNumber;
            case 'minus':
                return firstNumber - secondNumber;
            case 'multiply':
                return firstNumber * secondNumber;
            case 'divide':
                if (secondNumber !== 0) {
                    return firstNumber / secondNumber;
                } else {
                    return 'Indefinido';
                }
            default:
                return 'Operação Inválida';
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
            <input @change="(e:any) => {if (e.target) SetNumbers.firstNumber = (e.target as HTMLInputElement).value}" type="number" placeholder="Digite um número">
            <select @change="(e:any)=> { if (e.target) state.filter = (e.target as HTMLOptionElement).value }" class="btn btn-primary text-center d-flex me-2 ms-2">
                <option value="sum">+</option>
                <option value="minus">-</option>
                <option value="multiply">x</option>
                <option value="divide">&#247;</option>
            </select>
            <input  @change="(e:any) => {if (e.target) secondNumberInput = (e.target as HTMLInputElement).value}" type="number" placeholder="Digite um número">
        </div>
        <span>Resultado: {{ calculateResult() }}</span>
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
