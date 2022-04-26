<script lang="ts">
  import { createEventDispatcher } from 'svelte';
  export let index;
  export let number;
  const dispatch = createEventDispatcher();
  function Decrement(index) {
    if(number > 0) number = number - 1;
	dispatch('decrement', {
	index:index,
    number:number  
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

