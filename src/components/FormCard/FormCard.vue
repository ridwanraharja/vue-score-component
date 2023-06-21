<script setup>
let data = defineProps({
  title: String,
  description: String,
  manyItems: String,
  indexItem: Number,
});

import { ref, defineEmits } from "vue";

const emits = defineEmits(["handleSubmit"]);

const formInput = ref("");

const submitData = (event) => {
  event.preventDefault();
  emits("handleSubmit", data.indexItem, formInput.value); //this will trigger handleSubmit function in app.vue for update data
  formInput.value = ""; // Reset the input field after submission
};
</script>

<template>
  <div class="card">
    <div class="card-body">
      <form @submit.prevent="submitData" class="form-group mb-2">
        <h3>{{ data.title }}</h3>
        <label>{{ data.description }}</label>
        <input type="number" class="form-control" v-model="formInput" />
        <button type="submit" class="btn btn-secondary" @click="submitData">
          Check
        </button>
      </form>
    </div>
  </div>
</template>

<style scoped></style>
