<template>
  <div>
    <header>Who's that Pokemon!!</header>
    <Sprite :sprite="sprite"/>
    <Name :pokemonName="pokemonName"/>
  </div>
</template>

<script>
import axios from 'axios'
import Sprite from './Sprite'
import Name from './Name'

export default {
  name: 'MainPage',
  components: {
    Sprite,
    Name
  },
  data () {
    return {
      pokemonName: '',
      sprite: ''
    }
  },
  created () {
    axios({
      method: 'GET',
      url: 'https://pokeapi.co/api/v2/pokemon/56/'
    })
      .then(response => {
        this.pokemonName = response.data.name
        this.sprite = response.data.sprites.front_default
      })
      .catch(error => {
        this.error = error.response
      })
  }
}
</script>

<style>

</style>
