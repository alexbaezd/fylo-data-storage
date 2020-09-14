<template>
  <div class="icon">
    <img :src="require(`../assets/${image}`)" :alt="alt" />
  </div>
</template>

<script>
export default {
  props: {
    image: {
      type: String,
      required: true,
    },
    alt: {
      type: String,
      required: true,
    },
  },
};
</script>

<style>
.icon {
  background: var(--Very-Dark-Blue);
  display: grid;
  place-items: center;
  width: 48px;
  height: 48px;
  border-radius: 10px;
  margin: 0 0.4rem;
}
</style>
