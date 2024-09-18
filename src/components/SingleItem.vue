<script>
export default {
  data() {
    return {
      baseImgUrl: 'https://image.tmdb.org/t/p/',
      posterSize: 'w342',
      showDetails: false
    };
  },
  props: {
      title: String,
      originalTitle: String,
      language: String,
      vote: Number,
      posterPath: String
  },
  methods: {
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
  <div class="card" @mouseover="showDetails = true" @mouseleave="showDetails = false">
    <div class="poster" v-if="!showDetails">
      <img :src="baseImgUrl + posterSize + posterPath" alt="title" />
    </div>
    <div class="details" v-if="showDetails">
      <ul>
        <li>Titolo: {{ title }}</li>
        <li>Titolo Originale: {{ originalTitle }}</li>
        <li>Lingua: <img :src="getFlag(language)" class="flag-img" alt="" /></li>
        <li>
          Voto: {{ Math.ceil(vote / 2) }}
          <i v-for="x in Math.ceil(vote / 2)" :key="x" class="fa-solid fa-star text-warning"></i>
          <i v-for="x in (5 - Math.ceil(vote / 2))" :key="x" class="fa-regular fa-star text-warning"></i>
        </li>
      </ul>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use '../assets/scss/partials/mixins.scss' as *;

.card {
  position: relative;
  width: 220px;
  height: 320px;
  overflow: hidden;
  transition: all 0.3s ease;
  cursor: pointer;
}

.poster img {
  object-fit: cover;
  @include transition-height-width;
}

.details {
  position: absolute;
  top: 0;
  left: 0;
  background-color: rgba(0, 0, 0, 0.8);
  color: white;
  padding: 20px;
  box-sizing: border-box;
  @include opacity;
  @include transition-height-width;
}

.card:hover .details {
  opacity: 1;
}

.card:hover .poster img {
  @include opacity;
}

.flag-img {
  max-width: 25px;
}
</style>
