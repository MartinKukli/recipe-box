<template>
  <section id="RecipeDataList" class="w3-container w3-half w3-green">
    <h3>Instructions</h3>
    <i
      class="material-icons w3-xxlarge"
      style="cursor: pointer"
      @click="trashRecipe"
    >restore_from_trash</i>
    <h3>Ingredients</h3>
    <ul class="w3-ul">
      <li v-for="(ingredient, key) in this.data.ingredients" :key="key">{{ingredient}}</li>
    </ul>
    <h3>Directions</h3>
    <ul class="w3-ul">
      <li v-for="(direction, key) in this.data.directions" :key="key">{{direction}}</li>
    </ul>
  </section>
</template>

<script>
export default {
  name: "RecipeDataList",
  props: {
    data: Object
  },
  data: function() {
    return {
      recipeName: ""
    };
  },
  methods: {
    trashRecipe: function() {
      this.$emit("trash", this.data.name);
    }
  }
};
</script>

<style>
</style>