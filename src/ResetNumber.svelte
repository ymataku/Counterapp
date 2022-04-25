<script>
  import { createEventDispatcher } from 'svelte';
  export let index;
  const dispatch = createEventDispatcher();
	function ResetNumber(index) {
		dispatch('reset', {
			index:index
		});
  }
</script>
<button class="item" on:click={() => ResetNumber(index)}>0</button>
<style>
.item{
    margin: 10px 0;
    width:40px
  }
</style>

