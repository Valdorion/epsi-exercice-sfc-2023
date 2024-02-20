<script setup>
import HomePage from './components/HomePage.vue'
import "./assets/main.css"
</script>

<template>
  <HomePage/>

  <div>
    <ul v-if="results.length">
      <li v-for="result in results" :key="result.id">
        {{ result.title }}
      </li>
    </ul>
    <p v-else>No results found</p>
  </div>
</template>

<script>

export default {
  components: {
    HomePage
  },
  data() {
    return {
      results: []
    }
  },
  methods: {
    updateResults(results) {
      this.searchResults = results;
    }
  }
}
</script>