<template>
  <div class="card" v-if="job">
    <h1>{{ job.title }}</h1>
    <h3>job ID: {{ $route.params.id }}</h3>
    <p>{{ job.description }}</p>
  </div>
  <div v-else>
    <p>Loading...</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      job: null,
    };
  },
  mounted() {
    this.fetchJob();
  },
  methods: {
    fetchJob() {
      const jobId = this.$route.params.id;
      fetch(`http://localhost:3000/jobs/${jobId}`)
        .then((res) => res.json())
        .then((data) => {
          this.job = data;
        })
        .catch((err) => {
          console.error("Failed to fetch job details:", err.message);
          // Handle the error appropriately in the UI as well
        });
    },
  },
};
</script>

<style>
.card {
  width: 50%;
  margin: 10px auto;
  padding: 10px;
  background: rgb(220, 85, 36);
  border-radius: 10px;
  color: white;
}
</style>
