<template>
  <div v-if="this.finished" class="container">
    <div :data-resultado="score">
      <p>Você terminou! Seu score foi de: {{ score }} / {{ answered }}</p>
    </div>
    <div>
      <button @click="reload()" data-test="refazer" class="button">
        Refazer
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    score: Number,
    answered: Number,
    finished: Boolean
  },
  methods: {
    reload() {
      this.$emit("reload");
    }
  }
};
</script>
