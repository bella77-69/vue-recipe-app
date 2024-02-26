<script setup>
import { RouterLink, RouterView } from 'vue-router'

// import Recipe from './components/Recipe.vue';
</script>

<template>
  <header>
    <h1>Recipe App</h1>

    <div class="wrapper">
      <!-- <Recipe /> -->

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/recipe">Recipe</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>

</style>
