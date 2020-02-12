<template>
  <div class="currencySelector">
vers
<select v-model="currency">
       <option v-for="(rate,currencyKey) in rates " :key="currencyKey" :value="currencyKey">{{ currencyKey }} ({{ rate }})</option>
</select>
  
  </div>
</template>

<script>
export default {
  name: 'CurrencySelector',
  props: {
    rates: Object,

  }, 
  data(){
    return{
    'currency': 'USD',

  }
},
watch:{
currency: function(){
	this.$emit("currencyChanged", this.currency)
},
 // rates: function(){
 //    this.$emit("ratesChanged", this.rates[this.currency])
 //    console.log(this.rates[this.currency])  
 //    }
},
methods: {

}

}

</script>

<style>
.currencySelector{
	padding-top:1em;
}
</style>
