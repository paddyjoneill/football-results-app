<template>
  <div id="app">
    <side-bar></side-bar>
    <list-team :team-list="footballData"></list-team>
  </div>
</template>

<script>

import ListTeam from './components/ListTeam.vue';
import SideBar from './components/SideBar.vue';

export default {
  name: 'app',
  components: {
    'list-team': ListTeam,
    'side-bar': SideBar
  },
  data() {
    return {
      footballData: []
    }
  },
  mounted() {
    const myHeaders = new Headers();
    myHeaders.append('X-Auth-Token', 'b15e579370e848c4bed1021cf57a017d')

    const myRequest = new Request('https://api.football-data.org/v2/teams/66', {
      method: 'GET',
      headers: myHeaders,
      mode: 'cors',
      cache: 'default',
    });

    fetch(myRequest)
    .then((response) => response.json())
    .then((footballData) => {
      this.footballData = footballData;
    });
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
