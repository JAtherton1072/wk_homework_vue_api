<template>
  <div class="app">
    <h1>Studio Ghibli Films List</h1>
    <div class="main-container">
      <div><films-list :films="films"></films-list></div>
      <div><film-detail :film="selectedFilm"></film-detail></div>
      <favourites-list v-if='favourites.length' :favourites='favourites'></favourites-list>


    </div>
  </div>
</template>

<script>
import {eventBus} from '@/main.js';
import FilmsList from '@/components/FilmsList.vue';
import FilmDetail from '@/components/FilmDetail.vue';
import FavList from '@/components/FavList.vue'



export default {
  name: "app",
  components: {
    "films-list": FilmsList,
    "film-detail": FilmDetail,
    "favourites-list": FavList

  },


  data(){
    return{
      films: [],
      selectedFilm: null,
      favourites: []
    };


  },

  methods: {
    getFilms: function() {

      fetch('https://ghibliapi.herokuapp.com/films?items=50')
      .then(res => res.json())
      .then(films => this.films = films)


    }
  },




  mounted()  {
    this.getFilms();

    eventBus.$on('selected-film', (film) => {
    this.selectedFilm = film;
    });


    eventBus.$on('fav-selected', (film) => {
    if (!this.favourites.includes(film)) {this.favourites.push(film)};
    });


    eventBus.$on('fav-to-remove', (filmToRemove) => {
    this.favourites = this.favourites.filter(film => film.title !== filmToRemove.title);
    });



  }



};

</script>

<style lang="css" >

  .app {

   font-family: Palatino;
   background-color: black;
   color: white;
  }




  .main-container {
      display: flex;
      flex-flow: row;
      justify-content: space-between;


  }

</style>
