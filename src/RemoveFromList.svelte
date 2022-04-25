<script>
  import { createEventDispatcher } from 'svelte';
  export let index;
  const dispatch = createEventDispatcher();
	function RemoveFromList(index) {
		dispatch('remove', {
			index:index
		});
  }
</script>
<button class="item" on:click={() => RemoveFromList(index)}>×</button>
<style>
.item{
    margin: 10px 0;
    width:40px
  }
</style>

