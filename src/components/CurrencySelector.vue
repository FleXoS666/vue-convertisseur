<template>
  <div class="">

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
	console.log(this.currency)
  // this.updateValue()

}
},
methods: {
// updateCurrency(){
//   this.$emit("currencyChanged", this.currency)
//   console.log(this.currency)
}
}


</script>

<style>

</style>
