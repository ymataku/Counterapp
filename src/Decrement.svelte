<script lang="ts">
  import { createEventDispatcher } from 'svelte';
  export let index;
  export let titles;
  export let numbers;
  const dispatch = createEventDispatcher();
  function Decrement(index) {
    if(numbers[index] > 0) numbers[index] = numbers[index] - 1;
	dispatch('decrement', {
	index:index,
    titles:titles,
    numbers:numbers  
    });
  }
</script>
<button class="item" on:click={() => Decrement(index)}>-</button>
<style>
  .item{
    margin: 10px 0;
    width:40px;
    border:none;
  }
  @media(max-width:650px){
    .item {
    margin: 10px 0;
    width:8%;
    }
  }
</style>

