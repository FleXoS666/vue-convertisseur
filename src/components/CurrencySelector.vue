<template>
  <div class="">
<p>{{ rates }}</p>
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
methods: {

}

}
</script>

<style>

</style>
