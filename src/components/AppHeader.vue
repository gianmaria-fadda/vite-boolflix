<script>
import { store } from '../store.js';

export default {
  data() {
    return {
      store
    };
  },
  methods: {

  }
}
</script>

<template>
  <!-- 3) Utilizzo del componente -->
  <div class="d-flex justify-content-around bg-dark py-3">
    <div>
      <h1 class="text-danger">
        BOOLFLIX
      </h1>
    </div>

    <div>
      <form @submit.prevent="$emit('search')">
        <input v-model="store.searchText" type="text" placeholder="Cerca film o serie TV...">
        <button type="submit">
          Cerca
        </button>
      </form>
    </div>
  </div>

</template>

<style lang="scss">

</style>
