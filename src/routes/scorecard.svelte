<script>
  import { each } from 'svelte/internal';

  //Object Creation
  const players = {
    p1: { score: 0, hand: 0, playerName: 'Player 1' },
    p2: { score: 0, hand: 0, playerName: 'Player 2' },
    p3: { score: 0, hand: 0, playerName: 'Player 3' },
    p4: { score: 0, hand: 0, playerName: 'Player 4' }
  };
  let totalHand = 0;
  let lowScore = Infinity;
  //Reactive Statements
  $: totalHand =
    players.p1.hand + players.p2.hand + players.p3.hand + players.p4.hand;
  //Winning the Game
  $: if (
    players.p1.score > 100 ||
    players.p2.score > 100 ||
    players.p3.score > 100 ||
    players.p4.score > 100
  ) {
    for (var i in players) {
      if (players[i].score < lowScore) {
        lowScore = players[i].score;
        var key = i;
      } else if (players[i].score == lowScore) {
        alert('We have a tie!');
        var key = 'Nobody';
        break;
      }
    }
    alert('Winner is ' + key + '!');
  }

  //Functions
  function updateScore() {
    if (totalHand == 26) {
      players.p1.score += players.p1.hand;
      players.p2.score += players.p2.hand;
      players.p3.score += players.p3.hand;
      players.p4.score += players.p4.hand;
      players.p1.hand = players.p2.hand = players.p3.hand = players.p4.hand = 0;
    } else {
      alert('Hands must total 26!');
    }
  }

  export function resetScore() {
    players.p1.hand =
      players.p2.hand =
      players.p3.hand =
      players.p4.hand =
      players.p1.score =
      players.p2.score =
      players.p3.score =
      players.p4.score =
        0;
  }

  export function resetHand() {
    players.p1.hand = players.p2.hand = players.p3.hand = players.p4.hand = 0;
  }

  function pointsRemaining(hand) {
    return 26 - totalHand + hand;
  }

  function updateHands() {
    players.p1.hand = players.p1.hand;
    players.p2.hand = players.p2.hand;
    players.p3.hand = players.p3.hand;
    players.p4.hand = players.p4.hand;
  }

  function scoreButtons(player, amount) {
    if (amount == 26) {
      for (var i in players) {
        if (players[i] != player) {
          players[i].score += 26;
          players.p1.hand =
            players.p2.hand =
            players.p3.hand =
            players.p4.hand =
              0;
        }
      }
      return;
    }

    if (player.hand <= pointsRemaining(player.hand) - amount) {
      player.hand = player.hand + amount;
    }
    updateHands();
  }

  function validateInput(obj) {
    if (obj.hand > pointsRemaining(obj.hand)) {
      obj.hand = pointsRemaining(obj.hand);
    }
    updateHands();
  }
</script>

<div class="main">
  {#each Object.entries(players) as [label, player]}
    <div class="scoreCard">
      <div class="scoreCardUpper">
        <input type="text" class="playerName" bind:value={player.playerName} />
        <h1>{player.score}</h1>
      </div>
      <div class="scoreCardLower">
        <button class="scoreButton" on:click={() => scoreButtons(player, 26)}
          >Moon</button
        >
        <button class="scoreButton" on:click={() => scoreButtons(player, -1)}
          >-1</button
        >
        <input
          type="number"
          on:change={() => validateInput(player)}
          bind:value={player.hand}
          max={pointsRemaining(player.hand)}
        />
        <button class="scoreButton" on:click={() => scoreButtons(player, 1)}
          >+1</button
        >
        <button class="scoreButton" on:click={() => scoreButtons(player, 5)}
          >+5</button
        >
      </div>
    </div>
  {/each}
</div>

<div class="buttonContainer">
  Total: {totalHand} <br />
  <br /><button on:click={updateScore}>Submit!</button>
  <button on:click={resetHand}>Reset Hand</button>
</div>

<style>
  input {
    background: none;
    font-size: 18px;
    border: 2px solid black;
    border-radius: 10px;
    text-align: center;
    font-family: 'Paytone One', sans-serif;
    width: 90%;
    margin: 5px;
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
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    transition: all 0.3s ease-out;
    margin: 10px;
    flex-basis: 150px;
    max-width: 250px;
    height: 220px;
    flex-shrink: 1;
    flex-grow: 1;
    overflow: hidden;
  }

  .scoreCardUpper:hover {
    box-shadow: 0 4px 4px 0 rgb(0 0 0 / 23%);
  }
  .scoreCardLower:hover {
    box-shadow: 0 4px 4px 0 rgb(0 0 0 / 23%);
  }

  .scoreCardUpper {
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.12), 0 2px 4px rgba(0, 0, 0, 0.24);
    border-radius: 10px;
    width: 100%;
    height: 100%;
    margin: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .scoreCardLower {
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.12), 0 2px 4px rgba(0, 0, 0, 0.24);
    border-radius: 10px;
    width: 100%;
    height: 100%;
    margin: 10px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
  }

  h1 {
    font-size: 50px;
    font-family: 'Paytone One', sans-serif;
    margin: 10px;
  }

  button {
    display: inline-block;
    position: relative;
    margin: 10px;
    cursor: pointer;
    height: 50px;
    line-height: 50px;
    padding: 0 1.5rem;
    color: #000000;
    font-size: 15px;
    font-weight: 600;
    font-family: 'Paytone One', sans-serif;
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
  }
  .scoreButton {
    display: inline-block;
    position: relative;
    cursor: pointer;
    height: 25px;
    width: 50px;
    line-height: 25px;
    padding: 0 5px;
    margin: 5px;
    color: #000000;
    font-size: 12px;
    font-weight: 600;
    font-family: 'Paytone One', sans-serif;
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
  }

  button:hover {
    box-shadow: 0 4px 10px 0 rgb(0 0 0 / 23%);
  }

  .buttonContainer {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin: 50px;
  }

  /* Chrome, Safari, Edge, Opera */
  input::-webkit-outer-spin-button,
  input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }

  /* Firefox */
  input[type='number'] {
    -moz-appearance: textfield;
  }
</style>
