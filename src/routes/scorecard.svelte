<script>
  //Object Creation
  const players = {
    p1: { score: 0, hand: 0, playerName: 'Player 1' },
    p2: { score: 0, hand: 0, playerName: 'Player 2' },
    p3: { score: 0, hand: 0, playerName: 'Player 3' },
    p4: { score: 0, hand: 0, playerName: 'Player 4' }
  };
  let totalHand = 0;

  //Reactive Statements
  $: totalHand =
    players.p1.hand + players.p2.hand + players.p3.hand + players.p4.hand;
  $: if (
    players.p1.score > 100 ||
    players.p2.score > 100 ||
    players.p3.score > 100 ||
    players.p4.score > 100
  ) {
    alert('Winner!');
  }

  $: if (players.p1.hand > 26 - totalHand + players.p1.hand) {
    alert('Oh no!');
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
  function checkTotal(evt) {
    evt.value = 222;
    alert('you changed');
  }
</script>

<div class="main">
  <div class="scoreCard">
    <div class="scoreCardInner">
      <input
        type="text"
        class="playerName"
        bind:value={players.p1.playerName}
      />
      <h1>{players.p1.score}</h1>
    </div>
    <div class="scoreCardInner">
      <input
        type="range"
        bind:value={players.p1.hand}
        min="0"
        max={26 - totalHand + players.p1.hand}
        on:change={() => checkTotal(this)}
      />
      {players.p1.hand}
    </div>
  </div>

  <div class="scoreCard">
    <div class="scoreCardInner">
      <input
        type="text"
        class="playerName"
        bind:value={players.p2.playerName}
      />
      <h1>{players.p2.score}</h1>
    </div>
    <div class="scoreCardInner">
      <input
        type="range"
        bind:value={players.p2.hand}
        max={26 - totalHand + players.p2.hand}
      />
      {players.p2.hand}
    </div>
  </div>

  <div class="scoreCard">
    <div class="scoreCardInner">
      <input
        type="text"
        class="playerName"
        bind:value={players.p3.playerName}
      />
      <h1>{players.p3.score}</h1>
    </div>

    <div class="scoreCardInner">
      <input
        type="range"
        bind:value={players.p3.hand}
        max={26 - totalHand + players.p3.hand}
      />
      {players.p3.hand}
    </div>
  </div>

  <div class="scoreCard">
    <div class="scoreCardInner">
      <input
        type="text"
        class="playerName"
        bind:value={players.p4.playerName}
      />
      <h1>{players.p4.score}</h1>
    </div>
    <div class="scoreCardInner">
      <input
        type="range"
        bind:value={players.p4.hand}
        max={26 - totalHand + players.p4.hand}
      />
      {players.p4.hand}
    </div>
  </div>
</div>

<div class="buttonContainer">
  Total: {totalHand}
  <button on:click={updateScore}>Submit!</button>
</div>

<style>
  input {
    background: none;
    font-size: 18px;
    border: none;
    text-align: center;
    font-family: 'Paytone One', sans-serif;
    width: 90%;
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

  .scoreCardInner:hover {
    box-shadow: 0 4px 4px 0 rgb(0 0 0 / 23%);
  }

  .scoreCardInner {
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

  h1 {
    font-size: 50px;
    font-family: 'Paytone One', sans-serif;
    margin: 10px;
  }

  button {
    display: inline-block;
    position: relative;
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
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.12), 0 2px 4px rgba(0, 0, 0, 0.24);
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
</style>
