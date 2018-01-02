<template>
  <div class="text-center" id="app">
    <h1>Word Translator</h1>
    <h5>Powered by Vue.js</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data: function() {
    return {
      translatedText: ''
    }
  },
  methods: {
    translateText: function(text, language) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180102T212416Z.f6dd60528c80f3d2.23baed8beae83eead45b704a965b56842678a89a&lang=' + language + '&text=' + text)
        .then((response => {
          this.translatedText = response.body.text[0];
        }));
    }
  }
}
</script>

<style>

body {
  margin: 0;
  padding-top: 4rem;
  background: #fefefe;
}

h1 {
  margin-top: 1.5rem;
  margin-bottom: 1rem;
}

h5 {
  margin-bottom: 1.5rem;
}

</style>