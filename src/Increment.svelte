<script>
import { createEventDispatcher } from 'svelte';
export let index;
export let number;
const dispatch = createEventDispatcher();
  function Increment(index) {
    dispatch('increment', {
	   index: index ,
	});

  }
   
</script>

<button class="item" on:click={() => Increment(index)}>+</button>

<style>
.item{
    margin: 10px 0;
    width:40px
  }
</style>