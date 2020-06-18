<template lang="html">
  <div id="beersList">
    <ul>
      <beer-list-item v-for="(beer, index) in beers" :beer="beer" :key="index"></beer-list-item>
    </ul>
  </div>

</template>

<script>
import BeerListItem from './BeerListItem.vue';
export default {
  name: 'beers-list',
  props: ['beers'],
  components: {
    "beer-list-item": BeerListItem
  }
}
</script>

<style lang="css" scoped>
  #beersList {
    background: #eee;
    height: 400px;
    overflow-y: scroll;
    border: 1px solid #ccc;
  }

  #beersList ul {
    margin: 10px;
    padding: 0;
  }

  ::-webkit-scrollbar {
    -webkit-appearance: none;
    width: 7px;
  }

  ::-webkit-scrollbar-thumb {
    border-radius: 4px;
    background-color: rgba(0,0,0,.5);
    -webkit-box-shadow: 0 0 1px rgba(255,255,255,.5);
  }
</style>
