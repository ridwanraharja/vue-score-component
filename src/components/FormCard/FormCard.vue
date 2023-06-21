<script setup>
let data = defineProps({
  title: String,
  description: String,
  manyItems: String,
  indexItem: Number,
});

import { ref, defineEmits } from "vue";

const emits = defineEmits(["handleInput", "handleIncrement"]);
const formInput = ref(0);

const inputData = () => {
  return emits("handleInput", data.indexItem, formInput.value); //this will trigger handleInput function in app.vue for update data
};

const increment = (event) => {
  event.preventDefault();
  emits("handleIncrement", data.indexItem); //this will trigger handleIncrement function in app.vue for update data
};
</script>

<template>
  <div class="card">
    <div class="card-body">
      <form @submit.prevent="inputData" class="form-group mb-2">
        <h3>{{ data.title }}</h3>
        <label>{{ data.description }}</label>
        <input
          type="number"
          class="form-control"
          v-model="formInput"
          @input="inputData"
        />
        <button type="submit" class="btn btn-secondary mt-3" @click="increment">
          Check
        </button>
      </form>
    </div>
  </div>
</template>

<style scoped></style>
