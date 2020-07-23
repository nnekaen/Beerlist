<template>
  <v-app>
    <v-content>
      <img class="beer" src="./assets/beer.png">
      <h2  class="text-center my-5">Beer List</h2>
      <BeerList/>
    </v-content>
  </v-app>
</template>

<script>
import BeerList from './components/BeerList';

export default {
  name: 'App',

  components: {
    BeerList,
  },
};
</script>
<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.beer{
width:100px;
}
</style>
