<template>
  <v-container>
    <v-data-table
      :headers="headers"
      :items="result"
      :items-per-page="5"
      disable-pagination="true"
      hide-default-footer="true"
      class="elevation-1"
    ></v-data-table>
    <div class="text-center">
      <v-pagination
        v-model="page"
        :length="numberOfPages"
      ></v-pagination>
    </div>
  </v-container>
</template>

<script>
  export default {
    name: 'BeerList',

    data: () => ({
      result: [],
      page: 1,
      itemsPerRow: 5,
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

    computed: {
      numberOfPages() {
        return this.result.length / this.itemsPerRow;
      },
      list() {
        return [];
        // return this.result.slice();
      }
    },

    beforeMount() {
      fetch('https://api.punkapi.com/v2/beers?malt=extra_pale')
        .then(response =>  response.json())
        .then(data => this.result = data);
    }
  }
</script>
