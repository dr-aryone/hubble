<template>
  <a v-bind:href='link'>
    <div class='card'>
      <h1>{{ repo }}</h1>
      <h2>{{ description }}</h2>
      <h5>{{ author }}</h5>
      <p>{{ language }}</p>
      <div class='flex-row'>
        <img src="../assets/star.png"/>
        <p>{{ stars }}</p>
      </div>
      <div class='flex-row'>
        <img src="../assets/git-fork.png"/>
        <p>{{ forks }}</p>
      </div>
    </div> 
  </a>
</template>

<script>
export default {
  name: "RepoCard",
  props: {
    repo: String,
    description: String,
    author: String,
    language: String,
    link: String,
    stars: Number,
    forks: Number
  }
};
</script>

<style scoped>
a {
  text-decoration: none;
  color: teal;
}

.card {
  display: flex;
  max-width: 500px;
  flex-wrap: wrap;
  flex-direction: column;
  justify-content: center;
  border: 1px solid lightcoral;
  border-radius: 4px;
  padding: 20px;
  margin: 10px;
  min-height: 50vh;
}

.flex-row {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

.flex-row img {
  height: 20px;
  margin-right: 10px;
}
</style>

