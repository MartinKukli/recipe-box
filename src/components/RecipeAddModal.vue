<template>
  <section
    id="RecipeAddModal"
    v-bind:class="[display ? 'w3-show' : 'w3-hide', 'w3-modal']"
  >
    <div class="w3-modal-content">
      <header class="w3-container w3-blue">
        <span
          class="w3-button w3-display-topright w3-hover-light-blue"
          @click="$emit('hideAddModal')"
        >&times;</span>
        <h2>Add new recipe</h2>
      </header>
      <div class="w3-container w3-blue">
        <hr>
        <label>Name</label>
        <input class="w3-input" type="text" v-model="name">
        <label>Ingredients</label>
        <textarea class="w3-input" rows="3" cols="41" v-model="ingredients"></textarea>
        <label>Directions</label>
        <textarea class="w3-input" rows="3" cols="41" v-model="directions"></textarea>
        <hr>
        <div class="w3-center">
          <div class="w3-bar">
            <button class="w3-button w3-light-blue" @click="addRecipe">Add</button>
            <button class="w3-button w3-light-blue" @click="resetData">Reset</button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "RecipeAddModal",
  props: {
    display: Boolean
  },
  data: function() {
    return {
      name: "",
      ingredients: "",
      directions: ""
    };
  },
  methods: {
    addRecipe: function() {
      if (this.name !== "") {
        const data = {
          name: this.name,
          ingredients: this.ingredients.split("|"),
          directions: this.directions.split("|")
        };
        this.resetData();
        this.$emit("add", data);
      } else {
        alert("New recipe has no name");
      }
    },
    resetData: function() {
      this.name = this.ingredients = this.directions = "";
    }
  }
};
</script>

<style>
</style>