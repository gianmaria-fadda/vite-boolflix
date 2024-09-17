<script>
/* 
  Per importare ed utilizzare un componente dentro un altro devo SEMPRE seguire questi 3 passi:
  1) Importazione del componente
  2) Dichiarazione del componente
  3) Utilizzo del componente
*/
// 1) Importazione del componente

export default {
  data() {
    return {
    }
  },
  // 2) Dichiarazione del componente
  component: {

  },
  methods: {
    search() {
      console.log(this.searchText);
      
    }
  }
}
</script>

<template>
    <!-- 3) Utilizzo del componente -->
    <div class="d-flex justify-content-between">
    <div>
      <form @submit.prevent="search">
        <input type="text" placeholder="Cerca film o serie TV...">
        <button type="submit">
          Cerca
        </button>
      </form>
    </div>

    <div>
      <input type="text" placeholder="Cerca film o serie TV...">
      <button @click="search">
          Cerca
      </button>
    </div>
  </div>
</template>

<style lang="scss">
@use 'assets/scss/main' as *;
// Import all of Bootstrap's CSS
@import "bootstrap/scss/bootstrap";
</style>
