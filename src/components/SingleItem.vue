<script>
export default {
  data() {
    return {
      baseImgUrl: 'https://image.tmdb.org/t/p/',
      posterSize: 'w342'
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
    <ul>
      <li>
        <img :src="baseImgUrl + posterSize + posterPath" alt="title ">
      </li>
      <li>
        Titolo: {{ title }}
      </li>
      <li>
        Titolo Originale: {{ originalTitle }}
      </li>
      <li>
        Lingua: <img :src="getFlag(language)" class="flag-img" alt="">
      </li>
      <li>
        Voto: {{ Math.ceil(vote / 2) }}
        <i v-for="x in Math.ceil(vote / 2)" :key="x" class="fa-solid fa-star text-warning"></i>
        <i v-for="x in (5 - (Math.ceil(vote / 2)))" :key="x" class="fa-regular fa-star text-warning"></i>
      </li>
    </ul>
</template>

<style lang="scss" scoped>
img {
  max-width: 100%;

  &.flag-img {
    max-width: 25px;
  }
}
</style>
