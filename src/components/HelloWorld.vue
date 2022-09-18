<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>{{msg2}}</h1>
    <button v-on:click="increment(1)"> Increment</button>
    <p>{{count}}</p>

    <button v-for="number in evenList" :key="number"
      v-bind:class="getClass(number)"
      v-on:click="clicar(number)" 
      >

      <div> {{number}}
        <span v-if="isEvenList(number)"> Even</span>
        <span v-else> Odd</span>
      </div>
    </button>

    <input  
      type="text" 
      v-bind:value="'useds'"
      v-on:input="inputM"
       />
    {{value}}
    {{errorf}}

    <input type="radio"
      v-model="value2"
      value="a"
      />
    <input type="radio"
      v-model="value2"
      value="b"
      />
      {{value2}}

    <div v-if="isEven()" 
      v-bind:class="{reds: String}">
      Even
    </div>
    <div v-else>
      Odd
    </div>

    <hr/>

    <button v-for="numero in botoesApertados" :key ="numero"
      v-bind:class="getClass(numero)"
      v-on:click="clicar(numero)" 
      >
      <div>{{numero}}</div>
    </button>

  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'HelloWorld',
  data(){
    return {
      msg2: 'data teste',
      count: 0,
      value: 'user',
      value2: 'a',
      numbers: [1,2,3,4,5,6,7,8,9,10],
      imageSrv : "teste",
      errorM: ''
    }
  },
  props: {
    msg: String,
    botoesApertados: Object 
  },
  methods: {
    clicar(numero: number):void {
      this.$emit("escolhido", numero)
      console.log(numero)
    },
    inputM (event: any) : void{
      console.log(typeof event)
      this.value = (event.target.value)
    },
    increment(val:number) {
      /* this acessa qualquer coisa no data()*/ 
      this.count += val
    },
    isEven() {
      return this.count % 2 === 0
    },
    isEvenList(val: number) {
      return val % 2 === 0
    },
    getClass(val:number){
    return this.isEvenList(val) ?  'blue' : 'reds'
    }
  },
  computed: {
    evenList(){
      return this.numbers.filter(num => this.isEvenList(num))
    },
    errorf(){
      if (this.value.length < 5) {
        return 'Must ve greater than 5.'
      }else{
        return ''
      } 
    }
  }

});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .blue {
    color: blue;
  }

  .reds {
    color: red;
  }

</style>
