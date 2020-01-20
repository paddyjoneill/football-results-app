<template lang="html">
  <div class="">

  <div class="flex">
    <h1 id="matchheaderhome">{{ matchData.match.homeTeam.name }} : {{ matchData.match.score.fullTime.homeTeam}}</h1>
    <h1 id="matchheaderaway">{{ matchData.match.score.fullTime.awayTeam}} : {{ matchData.match.awayTeam.name }}</h1>
  </div>
  <div class="matchinfo">
    <h3>Venue: {{matchData.match.venue}}</h3>
  </div>

  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'match-details',
  props: ['match-data']
}
</script>

<style lang="css" scoped>

div.flex {
  display: flex;
}

.matchinfo {
  color: white;
  background: rgba(0,0,0,0.3);
  margin-left: 20px;
  margin-right: 20px;
}

#matchheaderhome {
  text-align: center;
  width:350px;
  height: 40px;
  color: white;
  background-color: red;
  margin-left: 30px;
  margin-right: 30px;
  padding: 20px;
  border-style: outset;
  font-size: 24px;
}

#matchheaderaway {
  text-align: center;
  width:350px;
  height: 40px;
  color: black;
  background-color: white;
  margin-left: 30px;
  margin-right: 30px;
  padding: 20px;
  border-style: outset;
  font-size: 24px;
}

</style>
