<template>
  <div class="progress card">
    <p class="progress-description">
      You’ve used
      <strong
        ><span>{{ used }}</span> GB</strong
      >
      of your storage
    </p>
    <ProgressBar :plan="plan" :size="getPercent" />
    <ProgressTooltip :num="plan - used" text="GB Left" />
  </div>
</template>

<script>
import ProgressTooltip from "./ProgressTooltip";
import ProgressBar from "./ProgressBar";

export default {
  components: {
    ProgressTooltip,
    ProgressBar,
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
  position: relative;
  width: 80%;
}

.progress-description {
  text-align: center;
  letter-spacing: 0.1px;
  font-size: 0.9rem;
}

@media (min-width: 768px) {
  .progress {
    width: 390px;
    align-self: flex-end;
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
