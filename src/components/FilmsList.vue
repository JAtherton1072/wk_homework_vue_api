<template>
  <div>
    <ul>
      <film-list-item v-for="film in films" :film="film" :key="film.id" ></film-list-item>
    </ul>
  </div>
</template>

<script>
import FilmListItem from './FilmListItem.vue'

export default {
  name: 'films-list',
  props: ['films'],
  components:{
    'film-list-item': FilmListItem
  }
}
</script>

<style>
</style>
