<template>
  <div class="hello">
    <h1>{{ value }} €uros</h1>
    
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    variant: String,
    value: Number,
    inputValue: Number
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
