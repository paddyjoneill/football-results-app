<template>
  <div id="app">
    <side-bar></side-bar>
    <premier-league v-if="selectedView==='league'":league-data="leagueData"></premier-league>
    <list-team v-if="selectedView==='team'" :team-list="teamData"></list-team>
    <player-details v-if="selectedView==='player'" :player-data="playerData"></player-details>
    <list-team-fixtures v-if="selectedView==='teamfixtures'" :fixture-data="selectedTeamMatches"></list-team-fixtures>
    <match-details v-if="selectedView==='matchdetails'" :match-data="matchData"></match-details>
  </div>
</template>

<script>
import {eventBus} from './main.js';

import SideBar from './components/SideBar.vue';
import PremierLeague from './components/PremierLeague.vue';
import ListTeam from './components/ListTeam.vue';
import PlayerDetails from './components/PlayerDetails.vue';
import ListTeamFixtures from './components/ListTeamFixtures.vue'
import MatchDetails from './components/MatchDetails.vue'


export default {
  name: 'app',
  components: {
    'side-bar': SideBar,
    'premier-league': PremierLeague,
    'list-team': ListTeam,
    'player-details': PlayerDetails,
    'list-team-fixtures': ListTeamFixtures,
    'match-details': MatchDetails
  },
  data() {
    return {
      leagueData: [],
      teamData: [],
      selectedTeamMatches: [],
      playerData: [],
      matchData: [],
      selectedView: null,
      header: null
    }
  },
  mounted() {
    this.fetchLeague(2021);
    eventBus.$on('selected-team',(id) => {
      this.fetchTeam(id);
    });
    eventBus.$on('selected-player', (id) => {
      this.fetchPlayer(id);
    });
    eventBus.$on('team-fixture-list', (id) => {
      this.fetchMatchesByTeam(id);
    });
    eventBus.$on('match-details', (id) => {
      this.fetchMatch(id);
    });
    eventBus.$on('switch-view', (view) => {
      console.log(view);
      this.selectedView = view;
    })

  },
  methods: {
    fetchData() {

      fetch(myRequest)
      .then((response) => response.json())
      .then((footballData) => {
        return footballData;
      });
    },

    fetchPlayer(id) {
      const myHeaders = new Headers();
      myHeaders.append('X-Auth-Token', 'b15e579370e848c4bed1021cf57a017d');

      let requestString = `https://api.football-data.org/v2/players/${id}`;

      const myRequest = new Request(requestString, {
        method: 'GET',
        headers: myHeaders,
        mode: 'cors',
        cache: 'default',
      });

      fetch(myRequest)
      .then((response) => response.json())
      .then((footballData) => {
        this.playerData = footballData;
        this.selectedView = 'player'
      });
    },

    fetchTeam(id) {
      const myHeaders = new Headers();
      myHeaders.append('X-Auth-Token', 'b15e579370e848c4bed1021cf57a017d');

      let requestString = `https://api.football-data.org/v2/teams/${id}`;

      const myRequest = new Request(requestString, {
        method: 'GET',
        headers: myHeaders,
        mode: 'cors',
        cache: 'default',
      });

      fetch(myRequest)
      .then((response) => response.json())
      .then((footballData) => {
        this.teamData = footballData;
        this.selectedView = "team"
      });
    },

    fetchMatchesByTeam(id) {
      const myHeaders = new Headers();
      myHeaders.append('X-Auth-Token', 'b15e579370e848c4bed1021cf57a017d');

      let requestString = `https://api.football-data.org/v2/teams/${id}/matches`;

      const myRequest = new Request(requestString, {
        method: 'GET',
        headers: myHeaders,
        mode: 'cors',
        cache: 'default',
      });

      fetch(myRequest)
      .then((response) => response.json())
      .then((footballData) => {
        this.selectedTeamMatches = footballData;
        this.selectedView = "teamfixtures"
      });
    },

    fetchMatch(id) {
      const myHeaders = new Headers();
      myHeaders.append('X-Auth-Token', 'b15e579370e848c4bed1021cf57a017d');

      let requestString = `https://api.football-data.org/v2/matches/${id}`;

      const myRequest = new Request(requestString, {
        method: 'GET',
        headers: myHeaders,
        mode: 'cors',
        cache: 'default',
      });

      fetch(myRequest)
      .then((response) => response.json())
      .then((footballData) => {
        this.matchData = footballData;
        this.selectedView = "matchdetails"
      });
    },

    fetchLeague(id) {
      const myHeaders = new Headers();
      myHeaders.append('X-Auth-Token', 'b15e579370e848c4bed1021cf57a017d');

      let requestString = `https://api.football-data.org/v2/competitions/${id}/standings/`;

      const myRequest = new Request(requestString, {
        method: 'GET',
        headers: myHeaders,
        mode: 'cors',
        cache: 'default',
      });

      fetch(myRequest)
      .then((response) => response.json())
      .then((footballData) => {
        this.leagueData = footballData;
        this.selectedView = 'league'
      });
    }
  }
}
</script>

<style>

@font-face {
  font-family: fourche;
  src: url(/fonts/sffourchebold.ttf);
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  /* font-family: fourche; */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  background-image: url("../public/images/old-trafford.jpg");
  background-size: cover;
  /* width:800px;
  height: 600px; */
}
</style>
