<template>
  <!-- https://dev-notes.eu/2018/05/passing-data-between-vue-components/ -->
  <section>
    <div class="container">
      <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->

      <!-- Source Section-->

      <h2 class="title is-4 mt-3">Word Translator</h2>
      <div class="is-flex">
        <form @submit.prevent="handleSubmit" class="m-3">
          <div
            class="is-flex is-flex-direction-row is-justify-content-flex-start mb-3"
          >
            <language-selector
              @LanguageSelected="handleEvent($event)"
              class="mr-2"
            />

            <language-selector @LanguageSelected="handleEvent($event)" />
          </div>

          <div
            class="is-flex is-flex-direction-row is-justify-content-flex-start mb-3"
          >
            <div class="field mr-2">
              <div class="control">
                <input
                  class="input"
                  type="text"
                  placeholder="Word to translate"
                  @keyup="this.wordToTranslate = $event"
                  v-model="wordToTranslate"
                />
              </div>
            </div>

            <div class="field">
              <input
                class="button is-primary"
                type="submit"
                value="Translate"
              />
              <!-- <button class="">Translate</button> -->
            </div>
          </div>
        </form>
      </div>

      <!-- Target Section  -->
      <div class="mt-2" style="width: 50%">
        <textarea
          class="textarea is-medium"
          name="target"
          type="text"
          cols="10"
          rows="5"
          v-model="translatedWord"
        ></textarea>
      </div>
    </div>
  </section>
</template>

<script>
import LanguageSelector from "./components/LanguageSelector.vue";

export default {
  name: "App",
  components: {
    LanguageSelector,
  },

  data() {
    return {
      sourceLanguage: "",
      wordToTranslate: "",
      translatedWord: "",
    };
  },
  methods: {
    handleEvent(event) {
      // console.log(event)
      this.sourceLanguage = event;
    },

    handleSubmit() {
      console.log(this.sourceLanguage);
      if (this.sourceLanguage !== "" && this.wordToTranslate !== "") {
        this.translatedWord =
          "Placeholder for translated word...key for API expired has expired";
      } else {
        console.log("An error has occurred");
      }

      // console.log(this.sourceLanguage);
      // console.log(this.wordToTranslate);
      // fetch('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170329T180255Z.3c18d2dc7b65d525.f23ed9a9efa992bded4ef96334e3c154f61d2dea&lang='+"es"+'&text='+"zapato")
      // .then((response) => {
      //   console.log(response);
      // });
    },
  },
};
</script>

<style lang="css">
</style>
