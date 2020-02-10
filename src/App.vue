<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/Money.png" class="image">
    <HelloWorld :value="inputValue" :result="result"/>

    <form @submit.prevent="updateValue">
      
      <input type="number" name="value" v-model="value">
      <input type="submit" name="" value="Convertir">
    </form>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },

  data(){
  return{
    'value' :  1,
    'inputValue': null,
    'rate': 0.8,
    'result': null,
  }
},
methods: {
updateValue(){
 this.inputValue = parseFloat(this.value)
  this.result= this.value * this.rate
  console.log(this.result)
},
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
