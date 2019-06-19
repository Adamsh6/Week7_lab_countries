<template lang="html">
<div v-if="selectedCountry">
<p>Name: {{selectedCountry.name}}</p>
<p>Capital: {{selectedCountry.capital}}</p>
<p>Population: {{selectedCountry.population}}</p>
<p>Languages spoken:</p>
<ul>
  <li v-for="language in selectedCountry.languages">- {{language.name}}</li>
</ul>
<img :src="selectedCountry.flag"/>
</div>


</template>

<script>
export default {
  name: "country-detail",
  props: ["selectedCountry"]
}
</script>

<style lang="css" scoped>
li {
  list-style: none;
}
img {
  width: 35%;
  border: 0.5px solid gray;
}
</style>
