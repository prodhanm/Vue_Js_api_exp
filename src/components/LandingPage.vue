<template>
  <section>
    <base-card>
      <h2>User Shopping Feedbacks</h2>
      <div>
        <base-button>Load all the Feedbacks</base-button>
      </div>
      <ul>
        <survey-results
          v-for="result in results"
          :key="result.id"
          :name="result.name"
          :rating="result.rating"
        >
        </survey-results>
      </ul>
    </base-card>
  </section>
</template>

<script>
import ResultsApp from "./ResultsApp.vue";
export default {
  data() {
    return {
      results: [],
    };
  },
  methods: {
    loadFeedbacks() {
      fetch("https://capone-node-default-rtdb.firebaseio.com/survey.json").then(
        (response) => {
          return response.json();
        }
      );
    },
  },
  mounted() {
    this.loadFeedbacks();
  },
  components: {
    surveyResults: ResultsApp,
  },
};
</script>

<style scoped></style>

