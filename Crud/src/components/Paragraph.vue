<!-- A template that we can reuse -->

<template>
  <div class="container">
    <p>
      {{ text }}
    </p>
  </div>
</template>
<script>
export default {
  name: "Paragraph",
  props: {
    text: {
      type: String,
      default: " Lorem ipsum dolor, sit amet consectetur adipisicing elit.",
    },
  },
};
</script>

<style scoped>
p {
  position: absolute;
  color: black;
  font-size: 1.2rem;
  letter-spacing: 2px;
  line-height: 1.8rem;
}

@media screen and (max-width: 1024px) {
  p {
    font-size: 1.1rem;
  }
}

@media screen and (max-width: 570px) {
  p {
    font-size: 1rem;
  }
}
</style>
