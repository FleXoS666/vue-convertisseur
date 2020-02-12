<template>
  <div class="deviseConverter">
    <h3>{{ baseValue }} EUR</h3>
    <h4>=</h4>
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
  margin:0.75em;
}
h3 {
  margin-bottom:0;
}
h4{
  margin-top:0.5em;
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
