<template>
  <div>
    <h1>BrewDog Menu Information</h1>
    <div class="main-container">
      <beers-list :beers="beers"></beers-list>
      <beer-detail :beer="selectedBeer"></beer-detail>
    </div>
  </div>
</template>

<script>
import { eventBus } from './main.js';
import BeerDetail from './components/BeerDetail.vue';
import BeersList from './components/BeersList.vue';

export default {
  data(){
    return {
      beers: [],
      favouriteBeers: [],
      selectedBeer: null  }
  },
  components: {
    "beers-list": BeersList,
    "beer-detail": BeerDetail
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(response => response.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) =>{
      this.selectedBeer = beer
    })
  }
}
</script>

<style lang="css" scoped>
h1 {
    text-align: center;
    color: #333;
  }
  .main-container {
    display: flex;
    justify-content: space-between;
    width: 80%;
    margin: 0 auto;
  }
</style>
