<!-- Main  -->

<template>
  <header>
    <footer>
      <div class="links">
        <RouterLink class="link" to="/">Home</RouterLink>
        <RouterLink class="link" to="/about">Learning</RouterLink>
        <!-- Footer in main  -->
      </div>
      <p class="footerText">This is example project</p>
    </footer>
  </header>

  <RouterView />
</template>

<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>


<!-- Basic styling  -->
<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body {
  width: 100vw;
  height: 100vh;
  display: flex;
  background-color: white;
  justify-content: center;
  align-items: center;
}

footer {
  display: flex;
  position: absolute;
  bottom: 10%;
  left: 10%;
  justify-content: space-around;
  align-items: center;
  width: 80%;
  background-color: grey;
  height: 6rem;
}

.link {
  color: black;
  text-decoration: none;
  cursor: pointer;
  font-size: 1.2rem;
  letter-spacing: 2px;
  margin: 1rem;
}

.link:hover {
  text-decoration: underline;
}

.footerText {
  color: black;
  font-size: 1.2rem;
  letter-spacing: 2px;
}

@media screen and (max-width: 1024px) {
  footer {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .footerText {
    margin-top: 2rem;
  }
}
</style>
