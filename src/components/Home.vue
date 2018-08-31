<template>
<div>

<div class='options'>
  <label class="label">Date Range: </label>
  <select v-model="selectedRange">
    <option v-bind:key='index' v-for="(option, index) in rangeOptions" v-bind:value="option.value">
      {{ option.text }}
    </option>
  </select>
</div>
<div class="responsive-cards">
  <div v-bind:key='index' v-for="(repo,index) in trendingRepos">
    <RepoCard
      v-bind:repo='repo.name'
      v-bind:author='repo.author'
      v-bind:description='repo.description'
      v-bind:link='repo.url'
      v-bind:language='repo.language'
      v-bind:stars='repo.stars'
      v-bind:forks='repo.forks'
    />
  </div>
  </div>
  </div>
</template>

<script>
import axios from "axios";
import RepoCard from "./RepoCard.vue";

export default {
  name: "Home",
  components: {
    RepoCard
  },
  data: function() {
    return {
      trendingRepos: [],
      rangeOptions: [
        { text: "Today", value: "daily" },
        { text: "Last Week", value: "weekly" },
        { text: "Last Month", value: "monthly" }
      ],
      selectedRange: "",
    };
  },
  beforeMount: function() {
    this.fetchTrending();
  },
  methods: {
    fetchTrending: function(range) {
      axios
        .get("https://github-trending-api.now.sh/repositories", {
          params: {
            langauge: 'javascript',
            since: range
          }
        })
        .then(response => (this.trendingRepos = response.data));
    }
  },
  watch: {
    selectedRange: function(value) {
      this.fetchTrending(value)
    },
  }
};
</script>

<style scoped>
.options {
  display: flex;
  flex-wrap: wrap;
  flex-basis: 100px;
  justify-content: center;
  align-items: center;
}
.label {
  font-size: 20px;
  margin-right: 5px;
}
.language-chips {
  border-radius: 20px;
  border: 1px solid lightblue;
  width: 150px;
  padding: 5px;
  margin: 5px;
  font-size: 20px;
}
.responsive-cards {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  flex-basis: 200px;
}
</style>