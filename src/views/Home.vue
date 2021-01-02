<template>
  <div class="container-main">
    <div id="nav">
      <router-link to="/" class="logo">moVUE</router-link>      
      <router-link to="/about" class="nav-link">About</router-link>
    </div>
    <form @submit.prevent="handleSubmit()">
      <div class="search-bar">
        <input type="search" autofocus v-model="search" placeholder="Search Movie">
        <img src="../assets/search.svg" alt="">
      </div>
      <button class="submit" type="submit">Search</button>
    </form>
    </div>
    <div v-if="movies !== undefined">
      <div class="" v-if="movies.length">
        <Movies :movies="movies" />
      </div>
    </div>
    <div class="error" v-else>
      No such Movie
    </div>
</template>

<script>
import { onMounted, onUnmounted, ref } from 'vue'
// @ is an alias to /src
import Movies from '../components/Movies'
import env from '../env.js'
export default {
  name: 'Home',
  components: {
    Movies
  },
  setup(){
    const search = ref("")
    const currentSearch = ref("")
    const movies = ref([])
    const errors = ref('')
    const handleSubmit = () => {
      if(search == '' || search == null){
        return
      }
      fetchMovie()
    }
    const fetchMovie = async () => {
      try{
        const temp = await fetch(`https://www.omdbapi.com/?apikey=${env.api_key}&s=${search.value}`);
        const result = await temp.json();

        movies.value = result.Search;
        // localStorage.setItem('movieSearch', search.value)
        localStorage.setItem('movies', JSON.stringify(movies.value))
      }
      catch(err){
        console.log(err);
      }
    }
    onMounted( async() => {
      // const temp = await fetch('http://www.omdbapi.com/?apikey=6b23572f&s='+ localStorage.getItem('movieSearch'));
      //   const result = await temp.json();
      //   movies.value = result.Search;
      movies.value = JSON.parse(localStorage.getItem('movies'))
    })
    return { search, handleSubmit , movies, errors }
  }
}
</script>
