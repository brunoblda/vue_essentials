<template>
  <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"
  v-on:escolhido="adicionarNumero"
  v-bind:botoesApertados="numerosHistorico"
  />

  <HelloNew greeting="New props"/>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import HelloWorld from './components/HelloWorld.vue';
import HelloNew from './components/HelloNew.vue';

export default defineComponent({
  name: 'App',
  components: {
    HelloWorld,
    HelloNew
  },
  methods:{
    adicionarNumero(numero: number):void{
      this.numerosHistorico.push(numero)
    }
  },
  data(){
    return{
      numerosHistorico: [] as number[]
    }
  }
});
</script>

<style>
</style>
