<template>
    <img :src="sprite" width="100" height="100"/>
</template>

<script>
export default {
  props: ['sprite'],
  name: 'Sprite'

}
</script>

<style>
img {
  width: 20%;
  height: 20%;
}
</style>
