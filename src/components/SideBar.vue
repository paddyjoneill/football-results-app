<template lang="html">
<div class="sidebar">
  <br>
  <button type="button" id="button">Friday 17/01/19 PM</button>
  <button type="button" id="button">Premier League</button>
  <button type="button" id="button">Manchester United</button>
  <button type="button" id="button">Marcus Rashford</button>


</div>
</template>

<script>
export default {
}
</script>

<style lang="css" scoped>
#button {
  width: 100px;
  height: 80px;
  border-style: inset;
  border-width: 5px;
  border-color: #00008B;
  color: white;
  background-color: #0074D9;
  font-size: 14px;
  font-weight: bold;
}

.sidebar {
  width: 150px;
  background-image: linear-gradient(#0074D9, #00008B);
  border-style: outset;
  border-left: 0px;
  border-top: 0px;
  border-bottom:0px;
}
</style>
