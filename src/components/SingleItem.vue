<script>
export default {
    props: {
        title: String,
        originalTitle: String,
        language: String,
        vote: Number
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
        Titolo: {{ title }}
        </li>
        <li>
        Titolo Originale: {{ originalTitle }}
        </li>
        <li>
        Lingua: <img :src="getFlag(language)" alt="">
        </li>
        <li>
        Voto: {{ vote }}
        </li>
    </ul>
</template>

<style lang="scss" scoped>
</style>
