<template>
  <v-data-table
    :headers="headers"
    :items="result"
    :items-per-page="5"
    class="elevation-1"
  ></v-data-table>
</template>

<script>
  export default {
    name: 'BeerList',

    data: () => ({
      result: null,
      headers: [
          {
            text: 'Name',
            align: 'start',
            sortable: true,
            value: 'name',
          },
          { text: 'Tagline', value: 'tagline' },
          
        ],
    }),

    beforeMount() {
      fetch('https://api.punkapi.com/v2/beers?malt=extra_pale')
        .then(response =>  response.json())
        .then(data => this.result = data);
    }
  }
</script>
