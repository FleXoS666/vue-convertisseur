<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/Money.png" class="image">
    <HelloWorld :baseValue="inputValue" :result="result" :currency="currency"/>

<img src="./assets/loader.gif" v-if="!rate">
    <form @submit.prevent="updateValue" v-if="rate">
      <select v-model="currency">

        <option v-for="(rate,currencyKey) in rates " :key="currencyKey" >{{ currencyKey }} ({{ rate }})</option>
      </select>
      <input type="number" name="baseValue" v-model="baseValue">
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
    'baseValue' :  1,
    'inputValue': 1,
    'rate': null,
    'rates': {},
    'currencyKey': {},
    'currency': 'USD',
    'inputCurrency': null,
    'result': null,
  }
},
mounted(){
  
  console.log(this.currency)
  this.init()
},
methods: {
updateValue(){
  this.inputCurrency=this.currency
 this.inputValue = parseFloat(this.baseValue)
 this.result= this.baseValue * this.rate
console.log(this.currency)
},
init(){
     console.log("start")
    var request = new XMLHttpRequest()
    request.open("GET","https://api.exchangeratesapi.io/latest")
    request.addEventListener("load", (event) => {
      var dataText=event.target.responseText;
      var data=JSON.parse(dataText); 
      this.rate= data.rates[this.currency];
      console.log(data.rates)
      this.rates= data.rates;

      // processConvert();
      console.log("updateRate ok");
    });
    request.send();
    // console.log(request.send())
    }
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
