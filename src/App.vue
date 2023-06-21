<script setup>
import ScoreComponent from "./components/Score/Score.vue";
import FormCardComponent from "./components/FormCard/FormCard.vue";
import { ref } from "vue";

const scoreItems = ref([
  {
    title: "Multiple Choice",
    scoreLength: 0,
    score: 0,
  },
  {
    title: "True or False",
    scoreLength: 0,
    score: 0,
  },
]);

const formItems = ref([
  {
    title: "Multiple Choice",
    description: "How many questions",
    manyItems: 0,
  },
  {
    title: "True or False",
    description: "How many questions",
    manyItems: 0,
  },
]);

const handleFormInput = (index, newValue) => {
  //get data from input in FormCard.vue & replace data in app
  scoreItems._value[index].scoreLength = newValue;
  formItems._value[index].manyItems = newValue;

  if (scoreItems._value[index].score >= formItems._value[index].manyItems) {
    scoreItems._value[index].score = 0;
    formItems._value[index].manyItems = 0;
    scoreItems._value[index].scoreLength = newValue;
  }
};

const handleScoreIncrement = (index) => {
  if (scoreItems._value[index].score < formItems._value[index].manyItems) {
    return scoreItems._value[index].score++;
  }
  return scoreItems._value[index].score;
};
</script>

<template>
  <section class="main-content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-12">
          <div class="card">
            <div class="card-body">
              <div class="row">
                <!--stage container-->
                <div class="stage col-12 col-lg-9 col-xl-9 mb-3">
                  <div v-for="(item, index) in formItems">
                    <FormCardComponent
                      v-bind="item"
                      class="mb-4"
                      @handleInput="handleFormInput"
                      @handleIncrement="handleScoreIncrement"
                      :indexItem="index"
                    />
                  </div>
                </div>
                <!--end stage container-->

                <!--score container-->
                <div class="col-12 col-lg-3 col-xl-3 side-content">
                  <h4>This activity includes</h4>
                  <ul class="activity-contents scrollbar-inner pl-0">
                    <li v-for="item in scoreItems">
                      <ScoreComponent v-bind="item" />
                    </li>
                  </ul>
                </div>
                <!--end score container-->
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.main-content {
  margin-top: 15px;
}

ul.activity-contents {
  padding-left: 0;
  list-style: none;
}
.activity-contents li {
  padding: 0.5rem 0;
  border-bottom: 1px solid #cccc;
}
</style>
