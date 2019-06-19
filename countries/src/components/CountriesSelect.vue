<template lang="html">
  <div>
    <label>Search for a country: </label>
  <select v-on:change="countrySelected" v-model="selectedCountry">
    <option  v-for="country in countries" :value="country">{{country.name}}</option>
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
      searchString: ""
    }
  },
  props: ["countries"],
  methods: {
    countrySelected(){

      partyBus.$emit('country-selected', this.selectedCountry)
    },
    textInputHandler(){
      let tempCountry = null
      this.countries.forEach((country) => {
        if(country.name.toLowerCase().startsWith(this.searchString.toLowerCase())){
          this.selectedCountry = country
          this.countrySelected()
          tempCountry = country
        }
      })
      //Next best match
      if(!tempCountry){
      this.countries.forEach((country) => {
        if(country.name.toLowerCase().includes(this.searchString.toLowerCase())){
          this.selectedCountry = country
          this.countrySelected()
        }
      })
    }

    }
  }
}
</script>

<style lang="css" scoped>
</style>
