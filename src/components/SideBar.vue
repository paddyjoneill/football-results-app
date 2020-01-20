<template lang="html">
<div class="sidebar">
  <br>
  <button type="button" id="button">{{dateString}}</button>
  <button type="button" id="button" v-on:click="viewLeague">Premier League</button>
  <button type="button" id="button">Manchester United</button>
  <button type="button" id="button">Marcus Rashford</button>
  <button type="button" id="button">About</button>


</div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'side-bar',
  data() {
    return{
      dateString: null
    }
  },
  methods: {
    viewLeague() {
      eventBus.$emit('switch-view', 'league')
    }
  },
  mounted () {
    this.dateString = new Date().toLocaleString();
    console.log(dateString);
  }
}
</script>

<style lang="css" scoped>
#button {
  width: 75px;
  height: 60px;
  border-style: inset;
  border-width: 5px;
  border-color: #00008B;
  color: white;
  background-color: #000078;
  font-size: 10px;
  font-weight: bold;
}

.sidebar {
  width: 85px;
  background-image: linear-gradient(#000078, #04011C);
  border-style: outset;
  border-left: 0px;
  border-top: 0px;
  border-bottom:0px;
  /* height: 600px; */
}
</style>
