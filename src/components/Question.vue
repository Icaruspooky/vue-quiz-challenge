<template>
  <div>
    <div class="container">
      <div data-test="pergunta" class="title">{{ question }}</div>
      <ul>
        <li v-for="(option, index) in options" :key="index">
          <button
            data-test="opcao"
            :disabled="disabled"
            class="button"
            :class="{
              'is-danger': option.danger,
              'is-success': option.success
            }"
            correct="option.correct"
            @click="getCorrectAnswer(option)"
          >
            {{ option.text }}
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    question: String,
    options: Array,
    score: Boolean,
    disabled: Boolean
  },
  data() {
    return {};
  },

  methods: {
    getCorrectAnswer(option) {
      if (option.correct) {
        option.success = true;
      } else {
        for (let i = 0; i < this.options.length; i++) {
          if (this.options[i].correct) {
            this.options[i].success = true;
          }
        }
        option.danger = true;
      }
      this.$emit("disable");
    }
  }
};
</script>
