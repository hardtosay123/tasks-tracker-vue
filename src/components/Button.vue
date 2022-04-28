<template>
  <button @click="onClick()" :style="{ backgroundColor: color }" class="btn">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: {
      type: String,
      default: "Unavailable",
    },
    color: {
      type: String,
      default: "steelblue",
    },
  },
  methods: {
    onClick() {
      this.$emit("onClick");
    },
  },
};
</script>

<style scoped>
</style>