<!-- A template that we can reuse -->

<template>
  <button @click="onClick">{{ value }}</button>
</template>

<script>
export default {
  name: "Button",
  props: {
    value: String,
  },
};
</script>

<style scoped></style>
