<template>
  <div class="app">
    <h1>Studio Ghibli Films List</h1>
    <div class="main-container">
      <div><films-list :films="films"></films-list></div>
      <div><film-detail :film="selectedFilm"></film-detail></div>

    </div>
  </div>
</template>

<script>
import {eventBus} from './main.js'
import FilmsList from './components/FilmsList.vue'
import FilmDetail from './components/FilmDetail.vue'


export default {
  data(){
    return{
      films: [],
      selectedFilm: null,

    }
  },
  components:{
     "films-list": FilmsList,
     "film-detail": FilmDetail

  },
  mounted(){
  fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(films => this.films = films)

    eventBus.$on('selected-film', (film) => this.selectedFilm = film)


  }
}
</script>

  <style lang="css" scoped>

  




    .main-container {
      display: flex;
      flex-flow: row;
      justify-content: space-between;
      font-family:fantasy;
    }

  </style>
