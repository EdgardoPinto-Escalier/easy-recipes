<template>
  <div class="add-recipe container">
    <h2 class="center-align purple-text">ADD NEW RECIPE</h2>
    <form @submit.prevent="AddRecipe">
      <div class="field title">
        <label for="title">RECIPE TITLE:</label>
        <input type="text" name="title" v-model="title">
      </div>
      <div class="field add-ingredient">
        <label for="add-ingredient">ADD INGREDIENT</label>
        <input type="text" name="add-ingredient">
      </div>
      <div class="field center-align">
        <button class="btn purple">ADD RECIPE</button>
      </div>
    </form>
  </div>
</template>

<script>
  export default{
    name: 'AddRecipe',
    data(){
      return {
        title: null
      }
    },
    methods: {
      AddRecipe(){
        console.log(this.title)
      }
    }
  }
</script>

<style>
  .add-recipe {
    margin-top: 60px;
    padding: 20px;
    max-width: 500px;
  }

  .add-recipe h2 {
    font-size: 2em;
    margin: 20px auto;
  }

  .add-recipe field {
    margin: 20px auto;
  }
</style>

