<script lang="ts">
  import Calculate from './Calculate.svelte';
</script>

<header>
	<h1>hello Counter Application</h1>
</header>
<main>
  <Calculate/>	
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