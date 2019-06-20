<template lang="html">
<div v-if="selectedCountry">
<p><em>Name:</em> {{selectedCountry.name}}</p>
<p><em>Capital:</em> {{selectedCountry.capital}}</p>
<p><em>Population:</em> {{selectedCountry.population}}</p>
<p><em>Languages spoken:</em></p>
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
  padding: 0.02em;
}
em {
  font-style: normal;
  font-weight: bold;
}
</style>
