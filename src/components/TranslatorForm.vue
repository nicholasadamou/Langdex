/* eslint-disable */

<template lang="pug">
  .container-fluid
    form(v-on:submit='formSubmit')
      .field.is-grouped.is-grouped-centered
          .control.is-expanded
            input.input(type='text', v-model='data', placeholder='Enter a Word or Phrase for Translation')
          p.control.has-icons-left
            span.select
              select(v-model='language')
                option(value='ru') Russian
                option(value='es') Spanish
                option(value='fr') French
                option(value='zh') Chinese
            span.icon.is-small.is-left
              i.fas.fa-globe
          button(type='submit').button.is-primary Translate
</template>

<script>
export default {
  name: "TranslatorForm",
  data() {
    return {
      data: "",
      language: ""
    };
  },
  created() {
    this.language = "es";
  },
  methods: {
    formSubmit(e) {
      e.preventDefault();
      this.$emit("formSubmit", this.data, this.language);
    }
  }
};
</script>
