<template>
  <div id="app">
    <main>
      <transition name="fade">
        <Brand v-if="show" :icons="icons" />
      </transition>
      <transition name="fade">
        <Progress v-if="show" :plan="storage" :used="used" />
      </transition>
    </main>
    <Attribution :author="author" :url="url" />
  </div>
</template>

<script>
import Brand from "./components/Brand";
import Progress from "./components/Progress";
import Attribution from "./components/Attribution";

export default {
  name: "App",
  components: { Brand, Progress, Attribution },
  data() {
    return {
      author: "Alex Báez",
      url: "https://alexbaez.dev",
      storage: 1000, //change
      used: 815, //change
      icons: [
        { id: 1, alt: "Icon Document", image: "icon-document.svg" },
        { id: 2, alt: "Icon Folder", image: "icon-folder.svg" },
        { id: 3, alt: "Icon Upload", image: "icon-upload.svg" },
      ],
      show: false,
    };
  },
  mounted() {
    this.show = !this.show;
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Raleway:wght@400;700&display=swap");
:root {
  --Gradient-color1: hsl(6, 100%, 80%);
  --Gradient-color2: hsl(335, 100%, 65%);
  --Pale-Blue: hsl(243, 100%, 93%);
  --Grayish-Blue: hsl(229, 7%, 55%);
  --Dark-Blue: hsl(228, 56%, 26%);
  --Very-Dark-Blue: hsl(229, 57%, 11%);
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background: url("./assets/bg-mobile.png") no-repeat center center fixed,
    var(--Dark-Blue);
  background-size: cover;
  color: white;
  font-family: "Raleway", sans-serif;
  font-size: 1rem;
}
#app {
  display: grid;
  place-items: center;
  grid-template-rows: auto 15px;
  height: 100vh;
}
main {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.card {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  background: var(--Dark-Blue);
  border-radius: 15px;
  padding: 1rem 2rem;
  margin: 0.5rem 0;
  box-shadow: 0px 10px 15px rgb(0, 0, 0, 0.5);
}

.fade-enter-active,
.fade-leave-active {
  transition: all 2s cubic-bezier(0.2, 0.82, 0.2, 1);
  transform: translateY(0px);
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
  transform: translateY(-100vh);
}
@media (min-width: 768px) {
  .card {
    margin: 0 1rem;
  }
}
@media (min-width: 1280px) {
  body {
    background: url("./assets/bg-desktop.png") no-repeat center bottom fixed,
      var(--Very-Dark-Blue);
    background-size: contain;
  }
  main {
    /* flex-wrap: nowrap; */
    align-items: end;
  }
  .card {
    margin: 0.5rem 1rem;
  }
}
</style>
