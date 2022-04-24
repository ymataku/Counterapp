<script lang="ts">
  import Result from './Result.svelte';
</script>

<header>
	<h1>Counter Application</h1>
</header>
<main>
  <Result/>	
</main>
<style>
  header {
    text-align: center
  }

  h1 {
    margin-top:100px;
  }

  main {
    text-align: center;
    padding: 1em;
    max-width: 600px;
    margin: 10px auto;
  }
</style>