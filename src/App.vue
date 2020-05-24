<template>
  <section id="app" class="w3-container w3-row">
    <section class="w3-row w3-center w3-blue">
      <h2 class="w3-panel">RecipeBox</h2>
    </section>
    <RecipeNamesList
      :names="this.recipes.map(recipe => recipe.name)"
      @new="() => this.displayAddModal = true"
      @click="updateSelectedRecipeData($event)"
    />
    <RecipeDataList :data="this.selectedRecipeData" @trash="trashRecipe($event)"/>
    <RecipeAddModal
      :display="this.displayAddModal"
      @hideAddModal="hideAddModal($event)"
      @add="addNewRecipe($event)"
    />
  </section>
</template>

<script>
import RecipeAddModal from "./components/RecipeAddModal";
import RecipeDataList from "./components/RecipeDataList";
import RecipeNamesList from "./components/RecipeNamesList";
export default {
  name: "App",
  components: {
    RecipeAddModal,
    RecipeDataList,
    RecipeNamesList
  },
  data: function() {
    return {
      displayAddModal: false,
      recipes: [
        {
          name: "RecipeName1",
          ingredients: ["ingredient11"],
          directions: ["directions11"]
        },
        {
          name: "RecipeName2",
          ingredients: ["ingredient21", "ingredient22"],
          directions: ["directions21", "directions22"]
        },
        {
          name: "RecipeName3",
          ingredients: ["ingredient31", "ingredient32", "ingredient33"],
          directions: ["directions31", "directions32", "directions33"]
        }
      ],
      selectedRecipeData: {}
    };
  },
  methods: {
    addNewRecipe: function(event) {
      this.displayAddModal = false;
      this.recipes.push(event);
    },
    hideAddModal: function() {
      this.displayAddModal = false;
    },
    updateSelectedRecipeData: function(event) {
      const recipeIndex = this.recipes.findIndex(
        recipe => recipe.name === event
      );
      this.selectedRecipeData = this.recipes[recipeIndex];
    },
    trashRecipe: function(name) {
      this.recipes = this.recipes.filter(recipe => recipe.name !== name);
      this.selectedRecipeData = this.recipes[0];
    }
  },
  mounted: function() {
    this.selectedRecipeData = this.recipes[0];
  }
};
</script>

<style>
</style>