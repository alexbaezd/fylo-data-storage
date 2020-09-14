<template>
  <div class="progress card">
    <p class="progress-description">
      You’ve used
      <strong
        ><span class="current">{{ used }}</span> GB</strong
      >
      of your storage
    </p>

    <div>
      <div class="progress-bar">
        <div class="progress-percentage" :style="{ width: getPercent }"></div>
      </div>
      <div class="progress-range">
        <p>0 GB</p>
        <p>{{ plan }} GB</p>
      </div>
    </div>

    <ProgressTooltip :num="plan - used" text="GB Left" />
  </div>
</template>

<script>
import ProgressTooltip from "./ProgressTooltip";

export default {
  data() {
    return {
      interval: null,
      count: 0,
      animation: {},
    };
  },
  mounted() {
    // this.interval = setInterval(() => {
    //   if (this.count === this.used) {
    //     return;
    //   }
    //   this.count++;
    // }, 2);
    console.log((this.used * 100) / this.plan);
  },
  beforeDestroy() {
    //clearInterval(this.interval);
  },
  props: {
    plan: {
      type: Number,
      required: true,
    },
    used: {
      type: Number,
      required: true,
    },
  },
  components: {
    ProgressTooltip,
  },
  computed: {
    getPercent() {
      return `${(this.used * 100) / this.plan}%`;
    },
  },
};
</script>

<style>
.progress {
  height: 160px;
  /* align-self: flex-end; */
  position: relative;
  width: 80%;
}

.progress-description {
  text-align: center;
  letter-spacing: 0.1px;
  font-size: 0.9rem;
}

.progress-bar {
  height: 18px;
  width: 100%;
  background-color: rgba(12, 18, 44, 0.5);
  border-radius: 10px;
  padding: 2px;
}
.progress-percentage {
  height: 100%;
  /* width: 81.5%; */
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
@media (min-width: 768px) {
  .progress {
    width: 390px;
  }
}
@media (min-width: 1280px) {
  .progress {
    height: 155px;
    width: 600px;
  }
  .progress p {
    text-align: left;
  }
}
</style>
