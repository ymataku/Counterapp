<script>
  import { createEventDispatcher } from 'svelte';
  export let index;
  const dispatch = createEventDispatcher();
	function Decrement(index) {
		dispatch('decrement', {
			index:index
		});
  }
</script>

<button class="item" on:click={() => Decrement(index)}>-</button>

<style>
.item{
    margin: 10px 0;
    width:40px
  }
</style>

