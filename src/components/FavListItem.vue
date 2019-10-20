<template lang="html">
  <li v-on:click="handleClick"> {{film.title}}</li>
</template>

<script>
import {eventBus} from '@/main.js';
export default {
  name: "fav-list-item",
  props: ['film'],
  methods: {

  }
}
</script>

<style lang="css" scoped>
</style>
