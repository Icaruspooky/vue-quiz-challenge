<template>
  <Index
    @reRender="forceReRender"
    :key="indexKey"
  />
</template>

<script>
import Index from "@/views/Index";

export default {
  components: {
    Index
  },
  data() {
    return {
      indexKey: 0
    };
  },
  methods: {
    forceReRender() {
      this.indexKey += 1;
    }
  }
};
</script>

<style lang="scss">
@import "@/theme/bulma.scss";
</style>
