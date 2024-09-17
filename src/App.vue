<script>
/* 
  Per importare ed utilizzare un componente dentro un altro devo SEMPRE seguire questi 3 passi:
  1) Importazione del componente
  2) Dichiarazione del componente
  3) Utilizzo del componente
*/
// 1) Importazione del componente

import axios from 'axios';

export default {
  data() {
    return {
      apiKey: 'dcdaddac05c607760f32e817be2c0842',
      searchText: '',
      movies: [],
      series: []
    }
  },
  // 2) Dichiarazione del componente
  component: {

  },
  methods: {
    search() {
      console.log(this.searchText);
      
      axios
        .get('https://api.themoviedb.org/3/search/movie', {
          params: {
            api_key: this.apiKey,
            query: this.searchText,
          }
        })
        .then((resp) => {
          console.log('Movies', resp.data);

          this.movies = resp.data.results;
        });

        axios
        .get('https://api.themoviedb.org/3/search/tv', {
          params: {
            api_key: this.apiKey,
            query: this.searchText,
          }
        })
        .then((resp) => {
          console.log('Series', resp.data);

          this.series = resp.data.results;
        });
    },
    getFlag(lang) {
      const validLang = {
        en: 'en.gif',
        it: 'it.gif',
        ja: 'jp.gif',
      };

      if (lang in validLang) {
        return '/img/flags/' + validLang[lang];
      } else {
        return '/img/flags/other-img.webp';
      }
    }
  }
}
</script>

<template>
    <!-- 3) Utilizzo del componente -->
    <div class="d-flex justify-content-between">
    <div>
      <form @submit.prevent="search">
        <input v-model="searchText" type="text" placeholder="Cerca film o serie TV...">
        <button type="submit">
          Cerca
        </button>
      </form>
    </div>

    <div>
      <input v-model="searchText" type="text" placeholder="Cerca film o serie TV...">
      <button @click="search">
          Cerca
      </button>
    </div>
  </div>

  <div>
    <h2>
      Movies
    </h2>
    <ol>
      <li v-for="(movie ,i) in movies" :key="i">
        <ul>
          <li>
            Titolo: {{ movie.title }}
          </li>
          <li>
            Titolo Originale: {{ movie.original_title }}
          </li>
          <li>
            Lingua: <img :src="getFlag(movie.original_language)" alt="">
          </li>
          <li>
            Voto: {{ movie.vote_average }}
          </li>
        </ul>

        <hr>

      </li>
    </ol>
  </div>

  <hr>

  <div>
    <h2>
      Series
    </h2>
    <ol>
      <li v-for="(series ,i) in series" :key="i">
        <ul>
          <li>
            Titolo: {{ series.name }}
          </li>
          <li>
            Titolo Originale: {{ series.original_title }}
          </li>
          <li>
            Lingua: <img :src="getFlag(series.original_language)" alt="">
          </li>
          <li>
            Voto: {{ series.vote_average }}
          </li>
        </ul>

        <hr>

      </li>
    </ol>
  </div>
</template>

<style lang="scss">
@use 'assets/scss/main' as *;
// Import all of Bootstrap's CSS
@import "bootstrap/scss/bootstrap";

img {
  max-width: 25px;
}
</style>
