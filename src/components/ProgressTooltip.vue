<template>
  <transition name="fade-tooltip">
    <div v-if="show" class="tooltip">
      <strong>{{ num }}</strong>
      <p>{{ text }}</p>
    </div>
  </transition>
</template>

<script>
export default {
  data() {
    return {
      show: false,
      time: null,
    };
  },
  mounted() {
    this.time = setTimeout(() => {
      this.show = !this.show;
    }, 1500);
  },
  destroyed() {
    clearTimeout(this.time);
  },
  props: {
    num: {
      type: Number,
      required: true,
    },
    text: {
      type: String,
      required: true,
    },
  },
};
</script>

<style>
.tooltip {
  display: flex;
  align-items: center;
  justify-content: center;
  align-self: center;
  position: absolute;
  bottom: -45px;
  width: 180px;
  height: 70px;
  background: white;
  color: var(--Very-Dark-Blue);
  border-radius: 10px;
  column-gap: 0.5rem;
}
.tooltip strong {
  font-size: 1.5rem;
  line-height: 1;
}
.tooltip p {
  text-transform: uppercase;
  font-weight: bold;
  font-size: 0.8rem;
  color: var(--Grayish-Blue);
  letter-spacing: 0.5px;
}

.fade-tooltip-enter-active,
.fade-tooltip-active {
  transition: opacity 2s;
}
.fade-tooltip-enter,
.fade-tooltip-leave-to {
  opacity: 0;
}

/* Tablet */
@media (min-width: 768px) {
  .tooltip {
    bottom: 0;
    right: 40px;
    top: -40px;
    width: 180px;
    height: 70px;
    border-radius: 10px 10px 0 10px;
  }
  .tooltip strong {
    font-size: 2.2rem;
  }
  .tooltip::after {
    content: "";
    position: absolute;
    right: 0;
    bottom: -12px;
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 0 20px 20px 0;
    border-color: transparent #ffffff transparent transparent;
  }
}
</style>
