<script>
 import Scorecard from './scorecard.svelte';
 let refresh = "./refresh.png";
</script>


<header>
  <div class="logo">
  <img src="/heart.png" class="headerimg">
  <h1>Svelte Hearts</h1>
</div>
<div>
  <img src="{refresh}" id="refresh">
</div>
</header>

  <Scorecard/>


<style>  
  :global(body) {
    font-family: Menlo, Consolas, Monaco, Liberation Mono, Lucida Console,
      monospace;
    background-color: #fafafa;
    
    margin: 0;
    padding: 0;
  }
  header {
    width: 100%;
    height: 100px;
    background: #FF4747;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
    align-items: center;
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
    padding-right: 10%;
    height: 64px;
  }

</style>
