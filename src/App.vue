<template>
  <v-app>
    <v-content>
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
