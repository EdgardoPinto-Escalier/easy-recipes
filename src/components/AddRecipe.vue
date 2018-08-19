<template>
  <div class="add-recipe container">
    <h2 class="center-align purple-text">ADD NEW RECIPE</h2>
    <form @submit.prevent="AddRecipe">
      <div class="field title">
        <label for="title">RECIPE TITLE:</label>
        <input type="text" name="title" v-model="title">
      </div>
      <div v-for="(ing, index) in ingredients" :key="index">
        <label for="ingredient">INGREDIENTS:</label>
        <input type="text" name="ingredient" v-model="ingredients[index]">
      </div>
      <div class="field add-ingredient">
        <label for="add-ingredient">ADD INGREDIENT:</label>
        <input type="text" name="add-ingredient" @keydown.tab.prevent="addIng" v-model="another">
      </div>
      <div class="field center-align">
        <p v-if="feedback" class="red-text">{{ feedback }}</p>
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
        title: null,
        another: null,
        ingredients: [],
        feedback: null
      }
    },
    methods: {
      AddRecipe(){
        console.log(this.title, this.ingredients)
      },
      addIng(){
        if(this.another){
          this.ingredients.push(this.another)
          this.another = null
          this.feedback = null
        } else {
          this.feedback = 'You must enter a value to add an ingredient'
        }
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

