<template lang="html">
  <div>
    <h3>{{country.name}}</h3>
    <p>({{country.alpha3Code}})</p>
    <p>Capital City: {{country.capital}}</p>
    <p>Population: {{country.population}}</p>
  </div>
</template>

<script>
export default {
  name:'country-detail',
  props:['country']
}
</script>

<style lang="css" scoped>
  div {
    width:400px;
    margin: 10px;
    padding: 10px;
    border: solid 1px black;
  }
</style>
