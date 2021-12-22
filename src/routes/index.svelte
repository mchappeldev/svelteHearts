<script>
  import Scorecard from './scorecard.svelte';
  let refresh = './refresh.png';
</script>

<svelte:head>
  <link
    href="https://fonts.googleapis.com/css2?family=Paytone+One&display=swap"
    rel="stylesheet"
  />
</svelte:head>
<header>
  <div class="logo">
    <img src="/heart.png" class="headerimg" />
    <h1>Svelte Hearts</h1>
  </div>
  <div>
    <img src={refresh} id="refresh" />
  </div>
</header>

<Scorecard />

<style>
  :global(body) {
    font-family: Menlo, Consolas, Monaco, Liberation Mono, Lucida Console,
      monospace;
    background: #ffbdbd;
    margin: 0;
    padding: 0;
    width: 100%;
  }
  header {
    width: 100%;
    height: 100px;
    background: #000;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.12), 0 2px 4px rgba(0, 0, 0, 0.24);
    align-items: center;
    background-size: contain;
  }
  h1 {
    padding-left: 10px;
    font-family: 'Paytone One', sans-serif;
    color: white;
  }

  .logo {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    padding: 10px;
    align-items: center;
  }

  .headerimg {
    height: 64px;
    top: 10px;
    left: 10px;
  }

  #refresh {
    padding: 25px;
    height: 50px;
  }
  #svelte {
    width: 100%;
  }
</style>
