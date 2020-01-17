<template lang="html">
  <div class="">
    <h1 id="playername">{{player.name}}</h1>
  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'player-details'
  props: ['player-data']
}
</script>

<style lang="css" scoped>
#playername {
  text-align: center;
  width:800px;
  color: white;
  background-color: red;
  margin-left: 30px;
  margin-right: 30px;
  padding: 20px;
  border-style: outset;
}
</style>
