<template>
  <v-container>
    <v-data-table
      v-model="selected"
      :headers="headers"
      :items="result"
      :page.sync="page"
      :items-per-page="itemsPerPage"
      hide-default-footer
      :single-select="percent"
      class="elevation-1"
      :search="search"
      @page-count="pageCount = $event"
    >
    <template v-slot:top>
        <v-text-field  v-model="search" label="Search peer" class="mx-4 search"></v-text-field>
      </template>
    <template v-slot:item.image_url="{ item }">
          <img :src=item.image_url style="width: 20px;" />
      </template>
    </v-data-table>
    <v-pagination
      v-model="page"
      :length="pageCount"
      circle
    ></v-pagination>
    <div class="text-center">
     <v-switch v-model="percent" label="Greater than 7%" value="7%"></v-switch>
    </div>
  </v-container>
</template>

<script>
  export default {
    name: 'BeerList',
     
    data () {
      return {
        page: 1,
        pageCount: 0,
        itemsPerPage: 5,
        percent: ['7%'],
        search: '',
      result: [],
      headers: [
       {text: "Thumbnail",
          align: "left",
          sortable: false,
          value: "image_url"
        },
          
          {
            text: 'Name',
            align: 'start',
            sortable: true,
            value: 'name',
          },
          { text: 'Tagline', value: 'tagline' },
          {text: 'ABV', value: 'abv' },

          {text: 'Description', value: 'description' },
         
        ],
        }
    },

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
