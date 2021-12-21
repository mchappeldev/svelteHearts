<script>
  let score1 = 0;
  let score2 = 0;
  let score3 = 0;
  let score4 = 0;
  let hand1  = 0;
  let hand2  = 0;
  let hand3  = 0;
  let hand4  = 0;


  function updateScore() {
    score1 += hand1;
    score2 += hand2;
    score3 += hand3;
    score4 += hand4;
    hand1 = 0;
    hand2 = 0;
    hand3 = 0;
    hand4 = 0; 
  }

</script>

<div class="main">
<div class= "scoreCard">
  <input type="text" class= "playerName"  value="Player 1:">
  <h1>{score1}</h1>
  <input type="number" bind:value={hand1}>
</div>

<div class= "scoreCard">
  <input type="text" class= "playerName" value="Player 2:">
  <h1>{score2}</h1>
  <input type="number" bind:value={hand2}>
</div>

<div class= "scoreCard">
  <input type="text" class= "playerName" value="Player 3:">
  <h1>{score3}</h1>
  <input type="number" bind:value={hand3}>
</div>

<div class= "scoreCard">
  <input type="text" class= "playerName" value="Player 4:">
  <h1>{score4}</h1>
  <input type="number" bind:value={hand4}>
</div>

</div>
<button on:click={updateScore}>Submit!</button>

<style>
input {
  background: none;
}

.main {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

.playerName {
  background: none;
  font-size: 18px;
  border: none;
}

.scoreCard {
  background: #fff;
  box-shadow: 0 2px 4px rgba(0,0,0,0.12), 0 2px 4px rgba(0,0,0,0.24);
  border-radius: 25px;
}

</style>