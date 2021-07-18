<template>
  <div>
    <div class="field">
      <label class="label mr-2">From: </label>
      <div class="control">
        <div class="select">
          <select
            name="languages"
            @change="LanguageSelected"
            v-model="selected"
          >
            <option value="english">English</option>
            <option value="spanish">Spanish</option>
            <option value="german">German</option>
            <option value="portuguese">Portuguese</option>
            <option value="french">French</option>
            <option value="italian">Italian</option>
          </select>
        </div>
      </div>
    </div>

   
  </div>
</template>

<script>
export default {
  components: {},

  data() {
    return {
      selected: "",
    };
  },
  methods: {
    LanguageSelected() {
      this.$emit("LanguageSelected", this.selected);
    },
  },
};
</script>

<style lang="css">
</style>



// Pass label property - pending