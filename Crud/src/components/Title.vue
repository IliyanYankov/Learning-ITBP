<!-- A template that we can reuse -->

<template>
  <h2>{{ title }}</h2>
</template>

<script>
export default {
  name: "Title",
  props: {
    title: {
      type: String,
      default: "Learning",
    },
  },
};
</script>
