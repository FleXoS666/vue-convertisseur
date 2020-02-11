<template>
  <div class="hello">
  <form @submit.prevent="updateValue" >

      <!-- <select v-model="currency">

        <option v-for="(rate,currencyKey) in rates " :key="currencyKey" :value="currencyKey">{{ currencyKey }} ({{ rate }})</option>
      </select> -->
      <input type="number" name="baseValue" v-model="baseValue">
      <input type="submit" name="" value="Convertir">
    </form>
  </div>
</template>

<script>
export default {
  name: 'UserInputForm',
  props: {
   
    
  }, data(){
    return{
     "baseValue": 1,
  }
}
}
</script>

<style>
h3 {
  margin: 0 0 20px;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.image{
 width: 200px;
}
</style>
