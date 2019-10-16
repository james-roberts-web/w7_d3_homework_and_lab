<template lang="html">
    
  <div class="container">

    <countries-list :countries='countries'></countries-list>
    <country-detail v-if='selectedCountry' :country='selectedCountry'></country-detail>
  </div>
</template>

<script>
import CountriesList from './components/CountriesList.vue';
import CountryDetail from './components/CountryDetail.vue';
import ListComponent from './components/ListComponent.vue'
import {eventBus} from './main.js';

export default {
  name: 'app',
  data () {
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted () {
    fetch('https://restcountries.eu/rest/v2/all')
    .then(result => result.json())
    .then(countries => this.countries = countries)

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country;
    });
  },

  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail,
    "list-item": ListComponent
  }
}

</script>

<style lang="css" scoped>
  .container {
    display: flex;
    justify-content: space-around;
    font-family: Helvetica, Arial, sans-serif;
  }
</style>
