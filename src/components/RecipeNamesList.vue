<template>
  <section id="RecipeNamesList" class="w3-container w3-half w3-green">
    <section>
      <h3>Recipes</h3>
      <i
        class="material-icons w3-xxlarge"
        style="cursor: pointer"
        @click="$emit('new')"
      >add_circle_outline</i>
    </section>
    <section>
      <input
        class="w3-input w3-border"
        type="text"
        placeholder="Search recipes"
        oninput="w3.filterHTML('recipeNames', 'li', this.value)"
      >
    </section>
    <section>
      <ul class="w3-ul recipeNames">
        <li
          class="w3-panel w3-border w3-hover-blue"
          style="cursor: pointer"
          v-for="(name, index) in names"
          :key="index"
          @click="$emit('click', name)"
        >{{name}}</li>
      </ul>
    </section>
  </section>
</template>

<script>
export default {
  name: "RecipeNamesList",
  props: {
    names: Array
  },
  data: function() {
    return {};
  },
  methods: {
    filterRecipesNames: function() {}
  }
};
</script>

<style>
</style>