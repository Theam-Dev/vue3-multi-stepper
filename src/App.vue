<template>
  <nav class="navbar navbar-expand-sm bg-dark navbar-dark">
  <!-- Links -->
  <div class="container">
    <ul class="navbar-nav">
    <li class="nav-item">
      <a class="nav-link" href="#">Tutoral Sharing 
       </a>
    </li>
    <li class="nav-item">
      <a class="nav-link" href="#">vue3-multi-stepper</a>
    </li>
  </ul>
  </div>
</nav>
<div class="container">
  
  <Vue3MultiStepper 
  v-model:step="step" 
  :tabs="tabs" 
  primaryColor1="blue" 
  primaryColor2="red" 
  backText="Go Back"
  nextText="Next" 
  doneText="Finish" 
  :loading="loading" 
  :finalize="handleFormSubmission" 
  :validateStep="validateStep">
    <template #1>
      <div class="form-group">
        <label for="username">UserName</label>
        <input type="text" class="form-control" v-model="username" placeholder="Enter username" id="username">
      </div>
      <div class="form-group">
        <label for="grad">Grad:</label>
        <input type="text" class="form-control" v-model="grad" placeholder="Enter grad" id="grad">
      </div>

    </template>
    <template #2>
      <div class="form-group">
        <label for="subject">Subject:</label>
        <input type="text" class="form-control" v-model="subject" placeholder="Enter subject" id="subject">
      </div>
      <div class="form-group">
        <label for="score">Score:</label>
        <input type="number" class="form-control" v-model="score" placeholder="Enter score" id="score">
      </div>
    </template>
    <template #3>
      <p>User Name: {{ username }}</p>
      <p>Grad : {{ grad }}</p>
      <p>Subject : {{ subject }}</p>
      <p>Score : {{ score }}</p>
    </template>
  </Vue3MultiStepper>
</div>

</template>

<script>
import "bootstrap/dist/css/bootstrap.min.css";
import { computed } from "vue";
import { Vue3MultiStepper } from "vue3-multi-stepper";

export default {
  components: {
    Vue3MultiStepper,
  },
  name: "App",
  data() {
    return {
      step: 1,
      loading: false,
      username: "",
      grad: "",
      subject: "",
      score: "",
      tabs: computed(() => {
        return [
          {
            title: "Personal",
            iconSuccess: null,
            isValid: true,
          },
          {
            title: "Info",
            iconSuccess: null,
            isValid: true,
          },
          {
            title: "Detail",
            iconSuccess: null,
            isValid: true,
          }
        ];
      }),
    };
  },

  methods: {
    async handleFormSubmission() {
      this.loading = true;
      setTimeout(() => {
        location.reload();
      }, 2000);
    },

    validateStep(step) {
      if (step === 1) {
        return this.step1Check();
      } else if (step === 2) {
        return this.step2Check();
      } else {
        return this.step3Check();
      }
    },

    step1Check() {
      return true;
    },
    step2Check() {

      return true;
    },
    step3Check() {
      return true;
    }
  },
};
</script>
<style>
.steppy-pane[data-v-bd8cdabb] {
  text-align: left;
}
</style>