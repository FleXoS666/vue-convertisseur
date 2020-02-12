<template>
  <div class="deviseConverter">
    <h3>{{ baseValue }} EUR</h3>
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
.deviseConverter{
  margin:20px;
}
h3 {
  margin:20px;
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
