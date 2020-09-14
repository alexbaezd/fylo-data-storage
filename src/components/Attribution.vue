<template>
  <div class="attribution">
    Challenge by
    <a href="https://www.frontendmentor.io?ref=challenge" target="_blank"
      >Frontend Mentor </a
    >. Coded by <a :href="url" target="_blank">{{ author }}</a
    >.
  </div>
</template>

<script>
export default {
  props: {
    author: {
      type: String,
      required: true,
    },
    url: {
      type: String,
      required: true,
    },
  },
};
</script>

<style>
.attribution {
  font-size: 12px;
}
.attribution a {
  color: var(--Pale-Blue);
}
</style>
