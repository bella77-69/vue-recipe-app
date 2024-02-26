<script>
import { v4 as uuidv4 } from "uuid";
export default {
  name: "Recipe",
  data() {
    return {
      recipe: {
        name: "",
        ingredients: "",
        steps: "",
      },
      recipes: [],
    };
  },
  computed: {
    formValid() {
      const { name, ingredients, steps } = this.recipe;
      return name && ingredients && steps;
    },
  },
  methods: {
    addRecipe() {
      if (!this.formValid) {
        return;
      }
      this.recipes.push({
        id: uuidv4(),
        ...this.recipe,
      });
    },
    deleteRecipe(index) {
      this.recipes.splice(index, 1);
    },
  },
};
</script>

<template>
    <form @submit.prevent="addRecipe">
      <div>
        <label>name</label>
        <input v-model="recipe.name" />
      </div>
      <div>
        <label>ingredients</label>
        <textarea v-model="recipe.ingredients"></textarea>
      </div>
      <div>
        <label>steps</label>
        <textarea v-model="recipe.steps"></textarea>
      </div>
      <button type="submit">add recipe</button>
    </form>
    <div v-for="(r, index) of recipes" :key="r.id">
      <h1>{{ r.name }}</h1>
      <h2>ingredients</h2>
      <div class="content">{{ r.ingredients }}</div>
      <h2>steps</h2>
      <div class="content">{{ r.steps }}</div>
      <button type="button" @click="deleteRecipe(index)">delete</button>
    </div>
  </template>
   
   <style>
   .content {
     white-space: pre-line;
   }
 
   form {
     display: grid;
     gap: 1rem;
   }
   form div {
     display: grid;
     gap: 0.5rem;
   }
   form label {
     font-weight: bold;
   }
   form input,
   form textarea {
     padding: 0.5rem;
   }
   form button {
     padding: 0.5rem;
   }
   form button:hover {
     background-color: #c0c0c0;
   }
 div {
   display: grid;
   gap: 1rem;
 }
 div h1 {
   font-size: 1.5rem;
 }
 div h2 {
   font-size: 1.25rem;
 }
 </style>