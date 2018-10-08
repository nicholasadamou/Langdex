/* eslint-disable */

<template lang="pug">
  #app
    section.hero
      .hero-body
        .container
          h1.title Langdex 
          h2.subtitle Powered by 
            a(href="https://vuejs.org/" target="_blank") Vue.js
            |, 
            a(href="https://tech.yandex.com/translate/" target="_blank") YanDex API
            |  and 
            a(href="https://bulma.io/" target="_blank") Bluma.
    .container
      translatorForm(v-on:formSubmit="translate")
    .container
      .section
        TranslatedOutput(v-bind:data="translated")
</template>

<script>
import TranslatorForm from "./components/TranslatorForm.vue";
import TranslatedOutput from "./components/TranslatedOutput.vue";

export default {
  name: "app",
  components: {
    TranslatorForm,
    TranslatedOutput
  },
  data: function() {
    return {
      translated: "Enter a word or phrase and see the translation here."
    };
  },
  methods: {
    translate: function(text, language) {
      this.$http
        .get(
          "https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170329T180255Z.3c18d2dc7b65d525.f23ed9a9efa992bded4ef96334e3c154f61d2dea&lang=" +
            language +
            "&text=" +
            text
        )
        .then(response => {
          this.translated = response.body.text[0];
        });
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Roboto", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
