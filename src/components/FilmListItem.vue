<template>
  <li v-on:click="handleClick">{{film.title}}</li>
</template>

<script>
import { eventBus } from '../main.js'
export default {
   name: 'film-list-item',
   props: ['film'],
   methods: {
       handleClick(){
           eventBus.$emit('selected-film', this.film)
       }
   }
}
</script>

<style>

</style>
