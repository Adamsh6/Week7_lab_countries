<template>
  <div class="main-container" id="app">
    <h2>Country Info!</h2>
    <countries-select :countries='countries'></countries-select>
    <country-detail :selectedCountry='selectedCountry'></country-detail>
  </div>
</template>

<script>


import {eventBus} from './main.js'
import CountryDetail from './components/CountryDetail.vue'
import CountrySelect from './components/CountriesSelect'

export default {
  name: 'app',
  data(){
    return{
      selectedCountry: null,
      countries: []
    }
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries)

    eventBus.$on('country-selected', (country) => {
    this.selectedCountry = country


    })
  },
  components: {
    "country-detail": CountryDetail,
    "countries-select": CountrySelect

  }
}
</script>



<style>

/* .main-container {
  display: flex;
  justify-content: space-between;
} */

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
