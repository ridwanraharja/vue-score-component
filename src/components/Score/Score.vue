<script setup>
defineProps({
  title: String,
  scoreLength: Number,
});
</script>

<template>
  <div class="score-item">
    <span>{{ title }}</span>
    <div
      class="score-wrapper border rounded-lg d-flex flex-column justify-content-between mb-2"
    >
      <div class="progress-wrapper">
        <b-progress
          :value="1"
          :max="scoreLength"
          variant="success"
        ></b-progress>
        <i
          class="bi bi-star-fill star animate__animated animate__heartBeat"
        ></i>
      </div>
      <div class="score">
        <strong>1/{{ scoreLength }}</strong>
      </div>
    </div>
  </div>
</template>

<style scoped>
.score-wrapper {
  padding: 0.75rem;
  position: relative;
  max-width: 200px;
}
.score-wrapper .star {
  color: #fdd835;
  font-size: 2rem;
  left: calc(100px - 1rem);
  line-height: 1;
  position: absolute;
  top: -12px;
}
.score {
  position: absolute;
  right: 0;
  margin-right: 0.5rem;
  line-height: 1;
}
.progress-wrapper {
  max-width: 100px;
  position: relative;
}
</style>
