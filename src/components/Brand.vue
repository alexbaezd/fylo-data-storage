<template>
  <div class="brand card">
    <img src="../assets/logo.svg" alt="Fylo Logo" />
    <div class="grid-icons">
      <BrandIcons
        v-for="icon in icons"
        :key="icon.id"
        :image="icon.image"
        :alt="icon.alt"
      />
    </div>
  </div>
</template>

<script>
import BrandIcons from "./BrandIcons";
export default {
  components: {
    BrandIcons,
  },
  props: {
    icons: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style>
.brand {
  align-items: flex-start;
  border-top-right-radius: 100px !important;
  height: 200px;
  width: 80%;
}
.grid-icons {
  display: flex;
  /* flex-direction: row; */
}
@media (min-width: 768px) {
  .brand {
    width: 250px;
  }
}
@media (min-width: 1280px) {
  .brand {
    width: 350px;
  }
}
</style>
