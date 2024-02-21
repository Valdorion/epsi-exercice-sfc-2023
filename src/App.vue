<script setup>
import "./assets/main.css"
</script>

<template>
  <HomePage @results-fetched="updateResults"/>

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
import HomePage from './components/HomePage.vue'

export default {
  components: {
    HomePage
  },
  data() {
    return {
      results: [] // Utilisez 'results' pour stocker les données récupérées
    };
  },
  methods: {
    updateResults(newResults) {
      this.results = newResults.data; // Met à jour 'results' avec les nouvelles données émises
    }
  }
}
</script>