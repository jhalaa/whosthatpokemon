<template>
  <div>
    <header>Who's that Pokemon!!</header>
    <div>
      <Sprite :sprite="sprite"/>
      <div>
        <Name />
      </div>
    </div>
    <footer class="footer navbar-fixed-bottom">
      <button @click="checkAnswer" class="btn-blck btn-primary">Check Answer</button>
      <button class="btn-blck btn-secondary">Next Pokemon</button>
    </footer>
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
  methods: {
    checkAnswer () {
      if (this.pokemonName === document.getElementById('pokemonName').value) {
        console.log(true)
      } else {
        console.log(false)
      }
    }
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
@font-face
{
font-family: pokemon-font;
src: url('./../assets/pokemonSolid.ttf')
}
header {
  font-family: 'pokemon-font', monospace;
  font-size: 127px;
  color: yellow;
  text-shadow: #0828de -13px 5px;
  -webkit-text-stroke-width: 8px;
  -webkit-text-stroke-color: blue;
}
button {
  width: 160px;
  height: 50px;
  margin: 30px;
}
body {
  background-color: black;
}
</style>
