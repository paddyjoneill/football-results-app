<template lang="html">
<div class="sidebar">
  <br>
  <button type="button" id="button">{{dateString}}</button>
  <button type="button" id="button">Premier League</button>
  <button type="button" id="button">Manchester United</button>
  <button type="button" id="button">Marcus Rashford</button>
  <button type="button" id="button">About</button>


</div>
</template>

<script>
export default {
  name: 'side-bar',
  data() {
    return{
      dateString: null
    }
  },
  mounted () {
    this.dateString = new Date().toLocaleString()
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
  background-color: #0074D9;
  font-size: 10px;
  font-weight: bold;
}

.sidebar {
  width: 85px;
  background-image: linear-gradient(#0074D9, #00008B);
  border-style: outset;
  border-left: 0px;
  border-top: 0px;
  border-bottom:0px;
  /* height: 600px; */
}
</style>
