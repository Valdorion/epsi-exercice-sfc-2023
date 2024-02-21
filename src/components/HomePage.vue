<script setup>
import '../assets/Style/homePage.css'
defineProps({
  msg: {
    type: String,
    required: true
  }
})
</script>

<template>
  <div>
    <form @submit.prevent="submitSearch">
      <!-- Champ de saisie lié à la variable searchQuery -->
      <input v-model="searchQuery" type="text" placeholder="Search..." />
      <!-- Sélection liée à la variable searchOption -->
      <select v-model="searchOption">
        <!-- Options de recherche -->
        <option value="all">All</option>
        <option value="title">Title</option>
        <option value="author">Author</option>
      </select>
      <!-- Bouton de soumission du formulaire -->
      <button type="submit">Search</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      searchQuery: '', // Stocke la requête de recherche de l'utilisateur
      searchOption: 'all' // Stocke l'option de recherche sélectionnée
    };
  },
  methods: {
    submitSearch() {
      if (this.searchQuery === '') return; // Vérifie que la requête n'est pas vide
      // Construit l'URL de recherche basée sur l'option et la requête
      const searchURL = `https://api.deezer.com/search/&q=${this.searchQuery}`;
      // Exécute la requête GET à l'API de Deezer
      axios.get(searchURL)
        .then(response => {
          this.$emit('results-fetched', response.data);
          console.log(response.data);
        })
        .catch(error => console.error(error)); // Gère les erreurs de requête
    }
  }
}
</script>