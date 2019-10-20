<template>
<article v-if="film">
      <h1> {{ film.title }} </h1>
      <button v-on:click="handleClick">Add to favourites</button>
      <button v-on:click="handleRemoveClick">Remove from favourites</button>

      <h3><span>Director</span>:</h3> {{ film.director }}
      <h3><span>Release Date</span>:</h3>{{ film.release_date }}
      <h3><span>Rating score</span>:</h3>{{ film.rt_score }}
      <h3><span>Description</span>:</h3> {{ film.description }}
      </article>
</template>

<script>
 import { eventBus } from '../main.js'
 export default {
  name: 'film-detail',
  props: ['film'],
  methods: {
    handleClick(){
      eventBus.$emit('fav-selected', this.film);
    },

    handleRemoveClick(){
      eventBus.$emit('fav-to-remove', this.film);
    }
  }
}
</script>

<style>
article{
    width:400px;
}
button {
  color:black;
  font-family: Palatino;
  background-color: #FA8334;
  border-radius: 30px;
  font-size: 100%;
  padding-bottom: 1px;
  padding-top: 2px;
}

</style>
