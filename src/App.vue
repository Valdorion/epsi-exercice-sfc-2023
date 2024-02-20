<script setup>
import HomePage from './components/HomePage.vue'
import "./assets/main.css"
</script>

<template>
  <nav>
    <form action="">
      <input type="text" placeholder="Search..." />
      <select name="" id="">
        <option value="all">All</option>
        <option value="title">Title</option>
        <option value="author">Author</option>
      <button type="submit">Search</button>
    </form>
  </nav>

  <main>
    <HomePage/>
  </main>
</template>
