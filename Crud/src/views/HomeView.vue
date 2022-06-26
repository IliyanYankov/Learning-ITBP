<!--   First Page -->
<template>
  <div class="container">
    <div class="img">
      <Image image="https://itbp.bg/assets/img/logo_itbp_new.png"></Image>
    </div>
    <div class="header">
      <Title title="Learning"></Title>
    </div>
    <div class="paragraph">
      <Paragraph
        text="Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aliquam suscipit
      alias facilis minus placeat repellendus iure eos eligendi ad, quaerat
      exercitationem corporis, aspernatur laborum laboriosam est? Ipsa quod, et
      aut accusamus placeat odit ad sit, rerum eos molestias quas, quisquam
      vitae esse. Facilis quia magni possimus labore odit nostrum, quasi eius
      officia repellendus numquam, illum quod sapiente corporis molestias earum?
      "
      ></Paragraph>
    </div>
  </div>
</template>

<script>
import Paragraph from "../components/Paragraph.vue";
import Image from "../components/Image.vue";
import Title from "../components/Title.vue";

export default {
  name: "Header",
  components: {
    Paragraph,
    Image,
    Title,
  },
  props: {
    text: String,
    title: String,
    image: String,
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Lobster&display=swap");

.header {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  top: 15%;
  font-size: 4rem;
  text-decoration: underline;
  color: #000;
  font-family: "Lobster", cursive;
}

img {
  position: absolute;
  width: 30%;
  right: 1%;
  top: 0%;
}

.paragraph {
  position: absolute;
  width: 60%;
  top: 45%;
  left: 50%;
  text-align: center;
  transform: translateX(-50%);
}
@media screen and (max-width: 1250px) {
  .header {
    font-size: 3rem;
    top: 20%;
  }
  .paragraph {
    width: 80%;
    top: 40%;
  }
}
@media screen and (max-width: 768px) {
  .header {
    top: 25%;
    font-size: 2.5rem;
  }
  .paragraph {
    width: 95%;
  }
}

@media screen and (max-width: 570px) {
  .header {
    top: 20%;
    font-size: 2rem;
  }

  .paragraph {
    top: 30%;
  }
}
</style>
