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
    'rate': 0,
    'result': null,
  }
},
mounted(){
  this.init()
console.log("ouech")

},
methods: {
updateValue(){
 this.inputValue = parseFloat(this.value)
  this.result= this.value * this.rate
},
init(){
     console.log("start")
    var request = new XMLHttpRequest()
    request.open("GET","https://api.exchangeratesapi.io/latest")
    



    request.addEventListener("load", function(event){
      var dataText=event.target.responseText;
      var data=JSON.parse(dataText); 
      this.rate= data.rates["USD"];
      // this.rates=data.rates;
      // processConvert();
      console.log(this.rate);

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
