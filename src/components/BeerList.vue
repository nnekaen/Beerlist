<template>
  <v-container>
  </v-container>
</template>

<script>
  export default {
    name: 'BeerList',

    data: () => ({
      result: null
    }),

    beforeMount() {
      fetch('https://api.punkapi.com/v2/beers?malt=extra_pale')
        .then(response =>  response.json())
        .then(data => this.result = data);
    }
  }
</script>
