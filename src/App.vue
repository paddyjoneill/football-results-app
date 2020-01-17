<template>
  <div id="app">
    <side-bar></side-bar>
    <premier-league v-if="selectedView==='league'":league-data="leagueData"></premier-league>
    <list-team v-if="selectedView==='team'" :team-list="teamData"></list-team>
    <player-details v-if="selectedView==='player'" :player-data="playerData"></player-details>
  </div>
</template>

<script>
import {eventBus} from './main.js';

import SideBar from './components/SideBar.vue';
import PremierLeague from './components/PremierLeague.vue';
import ListTeam from './components/ListTeam.vue';
import PlayerDetails from './components/PlayerDetails.vue';


export default {
  name: 'app',
  components: {
    'side-bar': SideBar,
    'premier-league': PremierLeague,
    'list-team': ListTeam,
    'player-details': PlayerDetails
  },
  data() {
    return {
      leagueData: [],
      teamData: [],
      playerData: [],
      selectedView: null,
      header: null
    }
  },
  mounted() {
    this.fetchLeague(2021);
    // this.fetchPlayer(3188);
    // this.fetchTeam(66);
    eventBus.$on('selected-team',(id) => {
      this.fetchTeam(id);
    })

  },
  methods: {
    fetchData(myRequest) {
      fetch(myRequest)
      .then((response) => response.json())
      .then((footballData) => {
        this.teamData = footballData;
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
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  background-image: url("../public/images/old-trafford.jpg");
  background-size: cover;
}
</style>
