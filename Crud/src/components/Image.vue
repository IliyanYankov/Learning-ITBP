<!-- A template that we can reuse -->

<template>
    <img :src="image" />
</template>

<script>
export default {
  name: "Image",
  props: {
    image: String,
  },
};
</script>

<style>

</style>
