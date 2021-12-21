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
  justify-content: space-evenly;
  align-items: center;
  margin: 50px, 20px;
}

.playerName {
  background: none;
  font-size: 18px;
  border: none;
  text-align: center;
}

.scoreCard {
  background: #fff;
  box-shadow: 0 2px 4px rgba(0,0,0,0.12), 0 2px 4px rgba(0,0,0,0.24);
  border-radius: 10px;
  height: 250px;
  width: 250px;
  font-family: 'Press Start 2P', cursive;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

button {
  display: inline-block;
    position: relative;
    cursor: pointer;
    height: 35px;
    line-height: 35px;
    padding: 0 1.5rem;
    color: #424242;
    font-size: 15px;
    font-weight: 600;
    font-family: "Roboto", sans-serif;
    letter-spacing: 0.8px;
    text-align: center;
    text-decoration: none;
    text-transform: uppercase;
    vertical-align: middle;
    white-space: nowrap;
    outline: none;
    border: none;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    border-radius: 2px;
    transition: all 0.3s ease-out;
    box-shadow: 0 2px 5px 0 rgb(0 0 0 / 23%);
}

</style>