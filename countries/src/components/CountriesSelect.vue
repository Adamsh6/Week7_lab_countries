<template lang="html">
  <div>
  <select v-on:change="countrySelected" v-model="selectedCountry">
    <option @select="countrySelected" v-for="country in countries" :value="country">{{country.name}}</option>
  </select>

   <input v-on:input="textInputHandler" v-model="searchString" type="text" ></input>
</div>
</template>

<script>
import {partyBus} from '../main'
export default {
  name: 'countries-select',
  data(){
    return{
      selectedCountry: null,
      testCountry: null,
      searchString: ""
    }
  },
  props: ["countries"],
  methods: {
    countrySelected(){

      partyBus.$emit('country-selected', this.selectedCountry)
    },
    textInputHandler(){
      this.countries.forEach((country) => {
        if(country.name.toLowerCase().startsWith(this.searchString.toLowerCase())){
          this.selectedCountry = country
          this.countrySelected()
        }
      })
    }
  }
}
</script>

<style lang="css" scoped>
</style>
