<template>
  <div>
    <div v-if="this.finished" class="container">
      <p>Você terminou! Seu score foi de:</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    total: Number,
    finished: Boolean
  }
};
</script>
