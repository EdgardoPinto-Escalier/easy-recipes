<template>
  <div class="index container">
    <div class="card" v-for="recipe in recipes" :key="recipe.id">
      <div class="card-content">
        <i class="material-icons delete" @click="deleteRecipe(recipe.id)">delete</i>
        <h2 class="purple-text">{{ recipe.title }}</h2>
        <ul class="ingredients">
          <!-- Here we loop through the ingredients using v-for -->
          <li v-for="(ing, index) in recipe.ingredients" :key="index">
            <span class="chip">{{ ing }}</span>
          </li>
        </ul>
      </div>
      <span class="btn-floating btn-large halfway-fab purple">
        <router-link :to="{ name: 'EditRecipe', params: {recipe_slug: recipe.slug}}"><i class="material-icons edit">edit</i></router-link>
      </span>
    </div>
  </div>
</template>

<script>
import db from '@/firebase/init'

export default {
  name: 'Index',
  data () {
    return {
      recipes: []
    }
  },
  methods: {
    deleteRecipe(id){
      // Delete doc from firestore
      db.collection('recipes').doc(id).delete()
      .then(() => {
        this.recipes = this.recipes.filter(recipe => {
          return recipe.id != id
        })
      }) 
    }
  },
  created(){
    // Here we get the data from firestore.
    db.collection('recipes').get() // We reference and get all the info for the collection.
    .then(snapshot => { // We return a snapshot (a view of the collection at this moment)
      snapshot.forEach(doc => { // We cicle through the snapshot and grab each document.
        let recipe = doc.data() // We grab the data from the object and assign it to a variable.
        recipe.id = doc.id // We add the id.
        this.recipes.push(recipe) // We push it to our array recipes []
      })
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.index {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 30px;
  margin-top: 60px;
}

.index h2 {
  font-size: 1.8em;
  text-align: center;
  margin-top: 0px;
}

.index .ingredients {
  margin: 30px auto;
}

.index .ingredients li {
  display: inline-block;
  text-transform: uppercase;
  font-weight: bold;
}

.index .delete {
  position: absolute;
  top: 6px;
  right: 6px;
  cursor: pointer;
  color: #aaaaaa;
  font-size: 1.8em;
}
</style>
