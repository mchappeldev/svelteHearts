<script>
 import Scorecard from './scorecard.svelte';
 let refresh = "./refresh.png";
</script>


<header>
  <div>
  <img src="/heart.png" class="headerimg">
  <h1>Svelte Hearts</h1>
</div>
<div>
  <img src="{refresh}" class="refresh">
</div>
</header>

  <Scorecard/>


<style>  
  header {
    width: 100%;
    align: left;
    background: #FF4747;
  }

  .headerimg {
    height: 128px;
    top: 10px;
    left: 10px;
  }

</style>
