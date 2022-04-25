<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();
  export let numbers;
  export let titles;
	function New() {
    titles = [...titles,"new"];
    numbers = [...numbers,0];
		dispatch('new', {
			titles:titles,
      numbers:numbers
		});
  }
</script>

<button class="new" on:click={ New }>new</button>

<style>
  .new{
    width:100%;
    margin-top:20px;
    background-color:#dcdcdc;
    border:none;
  }
  .new:hover{
    background-color:#ffffff;
  }
</style>

