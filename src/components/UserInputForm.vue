<template>
  <div class="hello">


  <form @submit.prevent="updateValue" >
      <input type="number" name="" v-model="inputValue">
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
     "inputValue": 1,
     
  }
},
methods: {
updateValue(){
  // this.inputValue = parseFloat(this.baseValue)
  this.$emit("inputChanged", this.inputValue)
  console.log(this.inputValue)
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
