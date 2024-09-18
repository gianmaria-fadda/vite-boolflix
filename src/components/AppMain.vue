<script>
import { store } from '../store.js';

import SingleItem from '../components/SingleItem.vue'

export default {
  data() {
    return {
      store
    };
  },
  methods: {

  },
  components: {
    SingleItem
  }
}
</script>

<template>
  <div>
    <h2>
      Movies
    </h2>
    <ol>
      <li v-for="(movie ,i) in store.movies" :key="i">

        <SingleItem
          :title="movie.title"
          :originalTitle="movie.original_title"
          :language="movie.original_language"
          :vote="movie.vote_average"
          :posterPath="movie.poster_path"
          />
          
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
      <li v-for="(series ,i) in store.series" :key="i">

        <SingleItem
          :title="series.name"
          :originalTitle="series.original_title"
          :language="series.original_language"
          :vote="series.vote_average"
          :posterPath="series.poster_path"
          />

        <hr>

      </li>
    </ol>
  </div>
</template>

<style lang="scss">

</style>
