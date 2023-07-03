<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Conteudo from './components/Conteudo.vue';
import Rodape from './components/Rodape.vue'

  const numeros = reactive({
    numero1: '',
    numero2: '',
    operacao: 'vazio',
  })

  const operacaoEscolhida = () => {
    const { numero1, numero2, operacao } = numeros;

    const divisaoOp = (numero1 / numero2).toFixed(2);

    const raizOp  = (numero1 ** (1/numero2)).toFixed(2);

    // console.log(numeros)

    if(numero1 === '' && numero2 === '' && operacao === 'vazio') {
      return 'Insira os dados'
    } else if (numero1 === '' && numero2 === '' && operacao !== 'vazio') {
      return 'Sem nenhum número'
    } else if ((numero2 === '' && operacao !== 'vazio') || (numero1 === '' && operacao !== 'vazio') ) {
      return 'Sem algum número'
    } else if (operacao === 'vazio') {
      return 'Operação inválida'
    } else {
      switch(operacao) {
        case 'soma':
          return (numero1 + numero2);
        case 'subtracao':
          return (numero1 - numero2);
        case 'divisao':
          return divisaoOp;
        case 'multiplicacao':
          return (numero1 * numero2);
        case 'exponenciacao':
          return (numero1 ** numero2);
        case 'raiz':
          return raizOp;
        case 'resto':
          return (numero1 % numero2);
        default:
          return 'Inválido'
        }
    }
  }


</script>

<template>
  <div class="container pb-5 bg-light">
    <Cabecalho />
    <Conteudo
      :insere-numero1="e => numeros.numero1 = Number(e.target.value)" 
      :insere-operacao="e => numeros.operacao = e.target.value"
      :insere-numero2="e => numeros.numero2 = Number(e.target.value)"
      :operacao="operacaoEscolhida()"
    />
    <Rodape />
  </div>
</template>

<style scoped>

</style>
