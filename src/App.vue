<template>
  <div>
    <h1>BrewDog Menu Information</h1>
    <div class="main-container">
      <beers-list :beers='beers'></beers-list>
    </div>
  </div>
</template>

<script>
import BeersList from './components/BeersList.vue';

export default {
  name: 'app',
  data(){
    return {
      beers: [],
      selectedBeer: null
    };
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(response => response.json())
    .then(beers => this.beers = beers)
  },
  components: {
    "beers-list": BeersList
  }
}
</script>

<style lang="css" scoped>
.main-container {
    display: flex;
    justify-content: space-between;
  }
</style>
