<template>
  <div class="">
    <h2>{{ baseValue }} </h2>
    <h3>{{ result }} {{ currency }}</h3>
  </div>
</template>

<script>
export default {
  name: 'DeviseConverter',
  props: {
    baseValue: Number,
    rate: Number,
    result: Number,
    inputValue: Number,
    currency: String,
    currencyKey: String,
    inputCurrency: String
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
</style>
