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
    <div class="d-flex justify-content-between">
    <div>
      <form @submit.prevent="$emit('search')">
        <input v-model="store.searchText" type="text" placeholder="Cerca film o serie TV...">
        <button type="submit">
          Cerca
        </button>
      </form>
    </div>

    <div>
      <input v-model="store.searchText" type="text" placeholder="Cerca film o serie TV...">
      <button @click="$emit('search')">
          Cerca
      </button>
    </div>
  </div>

</template>

<style lang="scss">

</style>
