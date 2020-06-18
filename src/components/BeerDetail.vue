<template lang="html">
  <div v-if="beer" id="beerDetail">
    <div id="beerDetailWrapper">
      <h2>{{beer.name}}</h2>
      <button v-on:click="addToFavourites">Love it!</button>
      <div id="flexWrapper">
        <div id="left">
          <p><span>Tagline</span>: {{beer.tagline}}</p>
          <p><span>Description</span>: {{beer.description}}</p>
          <p><span>Alcohol by Volume</span>: {{beer.abv}}</p>
        </div>
        <div id="right">
          <img :src="beer.image_url" :alt="beer.name">
        </div>
      </div>
    </div>
  </div>


</template>

<script>
import {eventBus} from '../main.js'
export default {
  name: 'beer-detail',
  props:['beer'],
  methods: {
    addToFavourites(){
      eventBus.$emit('favourite-beer', this.favouriteBeers)
    }
  }
}
</script>

<style lang="css" scoped>

#beerDetail {
  box-sizing: border-box;
  height: 400px;
  width: 60%;
  background: #eee;
  color: #222;
  padding: 10px;
  border: 1px solid #ccc;
}

#beerDetailWrapper {
  box-sizing: border-box;
  background: #fff;
  padding: 10px;
  height: 100%;
  border-radius: 3px;
}

#flexWrapper {
  display: flex;
  justify-content: space-between;
}

#left, #right {
  width: 45%;
}

#right img {
  width: 27%;
}

#left p:first-child {
  margin-top: 0;
}

h2 {
  margin: 10px 0 20px;
  padding: 0;
}

p span {
  font-weight: bold;
}

img {
  width: 50%
}

</style>
