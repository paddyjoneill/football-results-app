<template lang="html">
  <div class="">


  <h1 id="fixturestitle">Fixtures</h1>
  <table id="fixtures">
    <tr>
      <th>Date</th>
      <th>Home Team</th>
      <th>Score</th>
      <th>Away Team</th>
    </tr>
    <tr v-for="fixture in fixtureData.matches">
      <th>{{fixture.utcDate.substring(0,10)}}</th>
      <th>{{fixture.homeTeam.name}}</th>
      <th>{{fixture.score.fullTime.homeTeam}} - {{fixture.score.fullTime.awayTeam}}</th>
      <th>{{fixture.awayTeam.name}}</th>
    </tr>
  </table>
    </div>
</template>

<script>
export default {
  name: 'list-team-fixtures',
  props: ['fixture-data']
}
</script>

<style lang="css" scoped>

#fixturestitle {
  text-align: center;
  width:800px;
  color: white;
  background-color: red;
  margin-left: 30px;
  margin-right: 30px;
  padding: 20px;
  border-style: outset;
}

#fixtures {
  color: white;
  background: rgba(0,0,0,0.3);
  margin-left: 20px;
  margin-right: 20px;
  width: 860px;
}

</style>
