<template lang="html">
  <div class="">
    <h1 id="playername">{{playerData.name}}</h1>
    <table>
      <tr>
        <th>Position</th>
        <th>{{playerData.position}}</th>
      </tr>
      <tr>
        <th>Nationality</th>
        <th>{{playerData.nationality}}</th>
      </tr>
      <tr>
        <th>Date of Birth</th>
        <th>{{playerData.dateOfBirth}}</th>
      </tr>
      <tr>
        <th>Number</th>
        <th v-if="playerData.shirtNumber">{{playerData.shirtNumber}}</th>
      </tr>
    </table>
  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'player-details',
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

table {
  color: white;
  /* background-color: #000000;
  opacity: 0.5; */
  background: rgba(0,0,0,0.3);
  margin-left: 20px;
  margin-right: 20px;
  width: 860px;
  height:550px;
}

</style>
