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
    hand1 = 0; 
  }

</script>


<img src="/heart.png" class="headerimg">
<input type="text" id="player1Name" name="player1Name" value="Player 1:">
<h1>{score1}</h1>
<input type="number" bind:value={hand1}>

<input type="text" id="player2Name" name="player2Name" value="Player 2:">
<h1>{score2}</h1>
<input type="text" id="player3Name" name="player3Name" value="Player 3:">
<h1>{score3}</h1>
<input type="text" id="player4Name" name="player4Name" value="Player 4:">
<h1>{score4}</h1>

<button on:click={updateScore}>Submit!</button>


<style>
  :global(body) {
    font-family: Menlo, Consolas, Monaco, Liberation Mono, Lucida Console,
      monospace;
    background-color: #fafafa;
    max-width: 650px;
    margin: 32px auto;
    padding: 0 16px;
  }
  h1 {
    letter-spacing: -0.025em;
  }
  h2 {
    font-size: 18px;
  }
  ul {
    list-style: none;
    padding: 0;
    margin-top: 32px;
  }
  li {
    border: 1px solid #eaeaea;
    border-radius: 8px;
    margin-bottom: 16px;
    background-color: white;
    transition: 0.15s box-shadow ease-in-out;
  }
  li:hover {
    box-shadow: 0 5px 10px rgba(0, 0, 0, 0.12);
  }
  p {
    color: #666;
    font-size: 14px;
    line-height: 1.75;
  }
  a {
    color: #0070f3;
    text-decoration: none;
  }
  .card-link {
    padding: 8px 24px;
    display: block;
  }
  .link {
    transition: 0.15s text-decoration ease-in-out;
    color: #0761d1;
  }
  .link:hover {
    text-decoration: underline;
  }
  .headerimg {
    height: 128px;
    top: 10px;
    left: 10px;
  }
</style>
