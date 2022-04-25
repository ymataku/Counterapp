<script lang="ts">
  import { createEventDispatcher } from 'svelte';
  export let index;
  export let titles;
  export let numbers;
  const dispatch = createEventDispatcher();
    function RemoveFromList(index) {
      numbers.splice(index, 1)
      titles.splice(index, 1);
      numbers = numbers;
      titles = titles;
	  dispatch('remove', {
	    index:index,
        titles:titles,
        numbers:numbers
	});
  }
</script>
<button class="removelist" on:click={() => RemoveFromList(index)}>×</button>
<style>
  .removelist{
     margin: 10px 0;
     width:40px;
     border: none;
  }
  @media(max-width:650px){
    .removelist{
      margin: 10px 0;
      width:8%;
    }
  }
</style>

