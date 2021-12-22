<script>
  let score1 = 0;
  let score2 = 0;
  let score3 = 0;
  let score4 = 0;
  let hand1 = null;
  let hand2 = null;
  let hand3 = null;
  let hand4 = null;
  let player1 = 'Player 1';
  let player2 = 'Player 2';
  let player3 = 'Player 3';
  let player4 = 'Player 4';

  $: totalHand = hand1 + hand2 + hand3 + hand4;
  $: if (hand1 + hand2 + hand3 + hand4 === 26) {
    if (!hand1) {
      hand1 = 0;
    }
  }
  $: if (hand1 > 26 - totalHand + hand1) {
    alert("you can't do that idiot!");
  }

  function updateScore() {
    score1 += hand1;
    score2 += hand2;
    score3 += hand3;
    score4 += hand4;
    hand1 = null;
    hand2 = null;
    hand3 = null;
    hand4 = null;
  }
</script>

<div class="main">
  <div class="scoreCard">
    <input type="text" class="playerName" bind:value={player1} />
    <h1>{score1}</h1>
    <input type="number" bind:value={hand1} max={26 - totalHand + hand1} />
  </div>

  <div class="scoreCard">
    <input type="text" class="playerName" bind:value={player2} />
    <h1>{score2}</h1>
    <input type="number" bind:value={hand2} max={26 - totalHand + hand2} />
  </div>

  <div class="scoreCard">
    <input type="text" class="playerName" bind:value={player3} />
    <h1>{score3}</h1>
    <input type="number" bind:value={hand3} max={26 - totalHand + hand3} />
  </div>

  <div class="scoreCard">
    <input type="text" class="playerName" bind:value={player4} />
    <h1>{score4}</h1>
    <input type="number" bind:value={hand4} max={26 - totalHand + hand4} />
  </div>
</div>

<h1>{totalHand}</h1>

<div class="buttonContainer">
  <button on:click={updateScore}>Submit!</button>
</div>

<style>
  input {
    background: none;
    font-size: 18px;
    border: none;
  }

  .main {
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    align-items: center;
    margin: 50px 20px;
    flex-wrap: wrap;
  }

  .playerName {
    background: none;
    font-size: 25px;
    border: none;
    text-align: center;
    font-family: 'Paytone One', sans-serif;
    margin-top: 15px;
  }

  .scoreCard {
    background: #fff;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.12), 0 2px 4px rgba(0, 0, 0, 0.24);
    border-radius: 10px;
    font-family: 'Press Start 2P', cursive;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    transition: all 0.3s ease-out;
    margin: 10px;
    width: 250px;
    flex-shrink: 1;
    flex-grow: 1;
  }

  .scoreCard:hover {
    box-shadow: 0 4px 10px 0 rgb(0 0 0 / 23%);
  }

  h1 {
    font-size: 50px;
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
    font-family: 'Roboto', sans-serif;
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
    border-radius: 10px;
    transition: all 0.3s ease-out;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.12), 0 2px 4px rgba(0, 0, 0, 0.24);
  }

  button:hover {
    box-shadow: 0 4px 10px 0 rgb(0 0 0 / 23%);
  }

  .buttonContainer {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    margin: 50px;
  }
</style>
