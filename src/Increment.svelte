<script lang="ts">
  import { createEventDispatcher } from 'svelte';
  export let index;
  export let titles;
  export let numbers;
  const dispatch = createEventDispatcher();
  function Increment(index) {
  numbers[index] += 1 
  dispatch('increment', {
    index: index ,
    titles:titles,
    numbers:numbers
  });
}
</script>
<button class="increment" on:click={() => Increment(index)}>+</button>
<style>
  .increment{
    margin: 10px 0;
    width:40px;
    border: none;
  }
  @media(max-width:650px){
    .increment{
      margin: 10px 0;
      width:8%;
    }
  }
</style>