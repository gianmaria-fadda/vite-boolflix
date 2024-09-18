<script>
/* 
  Per importare ed utilizzare un componente dentro un altro devo SEMPRE seguire questi 3 passi:
  1) Importazione del componente
  2) Dichiarazione del componente
  3) Utilizzo del componente
*/
// 1) Importazione del componente

import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'
import axios from 'axios';
import { store } from './store.js';

export default {
  data() {
    return {
      store,
      apiKey: 'dcdaddac05c607760f32e817be2c0842',
      searchText: ''
    }
  },
  // 2) Dichiarazione del componente
  components: {
    AppHeader,
    AppMain
  },
  methods: {
    search() {
      console.log(this.store.searchText);
      
      axios
        .get('https://api.themoviedb.org/3/search/movie', {
          params: {
            api_key: this.apiKey,
            query: this.store.searchText,
          }
        })
        .then((resp) => {
          console.log('Movies', resp.data);

          this.store.movies = resp.data.results;
        });

        axios
        .get('https://api.themoviedb.org/3/search/tv', {
          params: {
            api_key: this.apiKey,
            query: this.store.searchText,
          }
        })
        .then((resp) => {
          console.log('Series', resp.data);

          this.store.series = resp.data.results;
        });
    }
  }
}
</script>

<template>
  <!-- 3) Utilizzo del componente -->
  <AppHeader @search="search()" />
  
  <AppMain />
</template>

<style lang="scss">
@use 'assets/scss/main' as *;
// Import all of Bootstrap's CSS
@import "bootstrap/scss/bootstrap";

img {
  max-width: 25px;
}
</style>
