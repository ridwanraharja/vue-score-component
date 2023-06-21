<script setup>
let data = defineProps({
  title: String,
  scoreLength: Number,
  score: Number,
});
// import { ref } from "vue";
// import { watch } from "vue";

// const target = ref(data.score);
// watch(target, (value) => {
//   if (value) {
//     target.value.classList.add("animate__animated", "animate__heartBeat");
//     target.value.addEventListener("animationend", () => {
//       target.value.classList.remove("animate__animated", "animate__heartBeat");
//     });
//   }
// });
</script>

<template>
  <div class="score-item">
    <span>{{ data.title }}</span>
    <div
      class="score-wrapper border rounded-lg d-flex flex-column justify-content-between mb-2"
    >
      <div class="progress-wrapper">
        <b-progress
          :value="data.score"
          :max="data.scoreLength"
          variant="success"
        ></b-progress>
        <i
          ref="target"
          class="bi bi-star-fill star animate__animated animate__heartBeat"
        ></i>
      </div>
      <div class="score">
        <strong>{{ data.score }}/{{ data.scoreLength }}</strong>
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
