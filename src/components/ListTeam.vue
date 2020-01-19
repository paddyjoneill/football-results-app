<template lang="html">
  <div class="teamlist">
    <h1 id="teamname">{{teamList.name}}</h1>
      <h2 id="displayselection">
        <button id="bigbutton">Squad</button>
        <button id="bigbutton" v-on:click="handleFixtureButtonClick(teamList.id)">Fixtures</button>
        <button id="bigbutton">Team Info</button>
      </h2>
    <ul>
      <li v-on:click="handleClick(player.id)" id="player" v-for="(player, index) in teamList.squad"><button id="button"></button>{{player.name}}</li>
    </ul>
  </div>

</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'list-team',
  props: ['team-list'],
  methods: {
    handleClick(playerId) {
      eventBus.$emit('selected-player', playerId );
    },
    handleFixtureButtonClick(teamId) {
      eventBus.$emit('team-fixture-list', teamId);
    }
  }
}
</script>

<style lang="css" scoped>


#teamname {
  text-align: center;
  width:800px;
  color: white;
  background-color: red;
  margin-left: 30px;
  margin-right: 30px;
  padding: 20px;
  border-style: outset;
}

#button {
  background-color: blue;
  border-style: outset;
  height: 20px;
  width: 40px;
  margin: 0px;
}

#bigbutton {
  width: 30%;
  height: 60px;
  border-style: inset;
  border-width: 5px;
  border-color: #00008B;
  color: white;
  background-color: #0074D9;
  font-size: 10px;
  font-weight: bold;
}



ul {
  columns: 2;
  -webkit-columns: 2;
  -moz-columns: 2;

  padding-top: 10px;
  padding-bottom: 10px;
  margin-left: 20px;
  margin-right: 20px;
  /* background-color: #000000;
  opacity: 0.5; */
  background: rgba(0,0,0,0.3);

}

#player {
  color: white;
  text-align: left;
  list-style-type: none;
  font-weight: bold;
}
</style>
