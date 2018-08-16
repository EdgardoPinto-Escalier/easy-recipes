<template>
  <div class="navbar">
    <nav class="nav-extended purple darken-4">
      <div class="nav-content">
        <router-link :to="{ name: 'Index' }">
          <span class="nav-title"><i class="material-icons"> restaurant</i> EASY RECIPES</span>
        </router-link>
        <a href="" class="btn-floating btn-large halfway-fab purple">
          <router-link :to="{ name: 'AddRecipe' }">
            <i class="material-icons">add</i>
          </router-link>
        </a>
      </div>
    </nav>
  </div>
</template>

<script>
  export default {
    name: 'Navbar',
    data() {
      return {

      }
    }
  }
</script>

<style>
  .navbar nav {
    padding: 0 20px;
  }

  span i.material-icons {
    font-size: 1.5em;
    vertical-align: middle !important;
    display: inline;  
    }
</style>

