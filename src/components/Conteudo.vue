<script setup>
    const props = defineProps(['insereNumero1', 'insereOperacao', 'insereNumero2', 'operacao'])
</script>

<template>
        <main class="row">
        <div class="col-12">
        <form>
        
            <input type="number" class="form-control" @keyup="props.insereNumero1" placeholder="Insira o primeiro número"  />

            <select @change="props.insereOperacao" class="form-control form-select">
            <option value="vazio"></option>
            <option value="soma">+</option>
            <option value="subtracao">-</option>
            <option value="divisao">/</option>
            <option value="multiplicacao">*</option>
            <option value="exponenciacao">**</option>
            <option value="raiz">Raiz</option>
            <option value="resto">%</option>
            </select>

            <input type="number" class="form-control" @keyup="props.insereNumero2" placeholder="Insira o segundo número"  />

            <div class="resposta form-control">
            <h1 >{{ props.operacao }}</h1> 
            </div>
        
        </form>
        </div>

    </main>
</template>

<style scoped>

form {
    display: grid;
    grid-template-columns: 30% 10% 30% 30%;

}

.form-control {
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    height: 100px;
    font-size: 30px;
}


.resposta {
    background-color: #fff;
}


</style>

