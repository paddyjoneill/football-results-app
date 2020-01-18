<template lang="html">
<div class="">
  <h1 id="leaguename">Premier League</h1>
  <table>
    <tr>
      <th>Team</th>
      <th>Played</th>
      <th>W</th>
      <th>D</th>
      <th>L</th>
      <th>GF</th>
      <th>GA</th>
      <th>Points</th>
    </tr>
    <tr v-for="(team, index) in leagueData.standings[0].table">
      <th v-on:click="handleTeamClick(index)">{{team.team.name}}</th>
      <th>{{team.playedGames}}</th>
      <th>{{team.won}}</th>
      <th>{{team.draw}}</th>
      <th>{{team.lost}}</th>
      <th>{{team.goalsFor}}</th>
      <th>{{team.goalsAgainst}}</th>
      <th>{{team.points}}</th>
    </tr>
  </table>
</div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'premier-league',
  props: ['league-data'],
  methods: {
    handleTeamClick(index) {
      eventBus.$emit('selected-team', this.leagueData.standings[0].table[index].team.id)
    }
  }
}
</script>

<style lang="css" scoped>

#leaguename {
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
  background-color: #000000;
  opacity: 0.5;
  margin-left: 20px;
  margin-right: 20px;
  width: 860px;
}

</style>
