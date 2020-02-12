<template>
  <div id="app">
<h1>Convertisseur de flouze</h1>
<img src="./assets/loader.gif" v-if="!rate">
<div v-if="rate">
    <img alt="Vue logo" src="./assets/euro.png" class="image">

    <UserInputForm @inputChanged="updateValue"></UserInputForm>
    
    <CurrencySelector @currencyChanged="updateCurrency"  :rates="rates"></CurrencySelector>

    <DeviseConverter :result="result" :currency="currency" :baseValue="baseValue"/>
 
</div>
</div>
</template>

<script>
import DeviseConverter from './components/DeviseConverter.vue'
import UserInputForm from './components/UserInputForm.vue'
import CurrencySelector from './components/CurrencySelector.vue'

export default {
  name: 'App',
  components: {
    DeviseConverter,
    UserInputForm,
    CurrencySelector
  },

  data(){
  return{
    'baseValue' :  1,
    'rates': {},
    'currencyKey': {},
    'currency': 'USD',
    'result': null,
  }
},

computed: {
    rate: function(){
    return this.rates[this.currency]
    }
  },


mounted(){
  console.log(this.currency)

  this.init()
},

methods: {
updateValue(value){
  this.baseValue=parseFloat(value)
  this.inputCurrency=this.currency
  this.result= value * this.rate
},
init(){
     console.log("start")
    var request = new XMLHttpRequest()
    request.open("GET","https://api.exchangeratesapi.io/latest")
    request.addEventListener("load", (event) => {
      var dataText=event.target.responseText;
      var data=JSON.parse(dataText); 
      // this.rate= data.rates[this.currency];
      console.log(data.rates)
      this.rates= data.rates;

      // processConvert();
      console.log("updateRate ok");
    });
    request.send();
    // console.log(request.send())
    },
    updateCurrency(currency){
      this.currency=currency
      this.updateValue(this.baseValue)
    },
    // updateRates(rate){
    //   this.rate=rate
    // }
},watch:{
  rates: function(){
   this.result= this.baseValue * this.rate
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
  margin-top: 40px;
}
</style>
