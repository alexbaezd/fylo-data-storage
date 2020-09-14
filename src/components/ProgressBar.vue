<template>
  <div>
    <div class="progress-bar">
      <div class="progress-percentage" :style="{ width: size }"></div>
    </div>
    <div class="progress-range">
      <p>0 GB</p>
      <p>{{ plan }} GB</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    size: {
      type: String,
      required: true,
    },
    plan: {
      type: Number,
      required: true,
    },
  },
};
</script>

<style>
.progress-bar {
  height: 18px;
  width: 100%;
  background-color: rgba(15, 17, 24, 0.5);
  border-radius: 10px;
  padding: 2px;
}
.progress-percentage {
  height: 100%;
  min-width: 15px;
  border-radius: 10px;
  position: relative;
  overflow: hidden;
  animation: animate-progress-bar 8s cubic-bezier(0.2, 0.82, 0.2, 1);
}
.progress-percentage::before {
  content: "";
  position: absolute;
  height: 100%;
  width: 100%;
  background-image: linear-gradient(
    75deg,
    hsl(6, 100%, 80%),
    hsl(335, 100%, 65%)
  );
  left: 0;
  top: 0;
}
.progress-percentage::after {
  content: "";
  position: absolute;
  top: 2px;
  width: 10px;
  right: 2px;
  bottom: 2px;
  border-radius: 10px;
  background: white;
}
.progress-range {
  margin-top: 10px;
  display: flex;
  justify-content: space-between;
  font-size: 0.8rem;
}

@keyframes animate-progress-bar {
  0% {
    width: 0;
  }
}
</style>
