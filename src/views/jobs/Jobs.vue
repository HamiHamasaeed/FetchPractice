<template>
  <h1>Jobs</h1>
  <div v-if="jobs.length">
    <div class="singleJob" v-for="job in jobs" :key="job.id">
      <router-link :to="{ name: 'JobDetails', params: { id: job.id } }">
        <h3>{{ job.title }}</h3>
      </router-link>
    </div>
  </div>
  <div v-else>
    <p>Loading...</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      jobs: [],
    };
  },
  mounted() {
    fetch("http://localhost:3000/jobs")
      .then((res) => res.json())
      .then((data) => {
        this.jobs = data;
      })
      .catch((err) => console.log(err.message));
  },
};
</script>

<style>
h3 {
  color: black;
  cursor: pointer;
  color: white;
}
.singleJob {
  margin: 10px;
  padding: 10px;
  background: royalblue;
  border-radius: 10px;
}
.singleJob:hover {
  background: rgb(110, 145, 251);
  cursor: pointer;
}
.singleJob a {
  text-decoration: none;
}
</style>
