<script>
export default {
  props: {
    results: {
      type: Array,
      required: true,
    },
    totalRes: {
      type: Number,
      required: true,
    },
  },
  computed: {
    resIndex() {
      let index = 0;

      this.results.forEach((current, i) => {
        if (current.min <= this.totalRes && this.totalRes <= current.max) {
          index = i;
        }
      });

      return index;
    },
  },
  data() {
    return {};
  },
};
</script>

<template>
  <div class="result">
    <div class="title">{{ results[resIndex].title }}</div>
    <div class="desc">{{ results[resIndex].desc }}.</div>
  </div>
</template>

<style lang="scss" scoped></style>
