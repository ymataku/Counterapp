<script lang="ts">
  import { createEventDispatcher } from 'svelte';
  export let index;
  export let number;
  const dispatch = createEventDispatcher();
  function ResetNumber(index) {
    number = 0; 
	dispatch('reset', {
	  index:index,
      number:number
	});
  }
</script>
<button class="reset" on:click={() => ResetNumber(index)}>0</button>
<style>
  .reset{
    margin: 10px 0;
    width:40px;
    border: none;
  }
  @media(max-width:650px){
    .reset{
      margin: 10px 0;
      width:8%;
    }
  }
</style>

