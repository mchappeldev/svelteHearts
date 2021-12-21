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

<div>
  <input type="text" id="player1Name" name="player1Name" value="Player 1:">
  <h1>{score1}</h1>
  <input type="number" bind:value={hand1}>
</div>

<div>
  <input type="text" id="player2Name" name="player2Name" value="Player 2:">
  <h1>{score2}</h1>
  <input type="number" bind:value={hand2}>
</div>

<div>
  <input type="text" id="player3Name" name="player3Name" value="Player 3:">
  <h1>{score3}</h1>
  <input type="number" bind:value={hand3}>
</div>

<div>
  <input type="text" id="player4Name" name="player4Name" value="Player 4:">
  <h1>{score4}</h1>
  <input type="number" bind:value={hand4}>
</div>

<button on:click={updateScore}>Submit!</button>


