<script lang="ts">
  import { createEventDispatcher } from 'svelte';
  export let titles;
  export let numbers;
  const dispatch = createEventDispatcher();
  
  function Increment(index) {
  numbers[index] += 1;
  dispatch('dispatch', {
    index: index ,
    titles:titles,
    numbers:numbers
  });
  }
  function ResetNumber(index) {
    numbers[index] = 0; 
	dispatch('dispatch', {
	  index:index,
      titles:titles,
      numbers:numbers
	});
  }
  function RemoveFromList(index) {
      numbers.splice(index, 1)
      titles.splice(index, 1);
      numbers = numbers;
      titles = titles;
	  dispatch('dispatch', {
	    index:index,
        titles:titles,
        numbers:numbers
	});
  }
  function Decrement(index) {
    if(numbers[index] > 0) numbers[index] = numbers[index] - 1;
	dispatch('dispatch', {
	index:index,
    titles:titles,
    numbers:numbers  
    });
  }
  function New() {
    titles = [...titles,"new"];
    numbers = [...numbers,0];
		dispatch('dispatch', {
			titles:titles,
      numbers:numbers
		});
  }
</script>
{#each titles as title, index}
  <div class="counter">
    <input class="counter_title" bind:value = { title } >
    <span class="counter_items">
      <button class="item number">{ numbers[index] }</button>
      <button class="item" on:click={() => Increment(index)}>+</button>
      <button class="item" on:click={() => Decrement(index)}>-</button>
      <button class="item" on:click={() => ResetNumber(index)}>0</button>
      <button class="item" on:click={() => RemoveFromList(index)}>×</button>
    </span>
  </div>
{/each} 

<button class="new" on:click={ New }>new</button>
<h3>title: { titles }</h3>
<style>
.counter{
    margin-top:5px;
    width:100%;
    margin:5px auto;
    border-radius: 3px;
    box-shadow: 2px 2px 4px;
  }
  .counter_title{
    width: 60%;
    margin-left:0;
    border: none;
  }
  .counter_items{
    width: 40%;
    margin-right:0;
  }
  .item{
    margin: 10px 0;
    width:40px;
    border:none;
  }
  @media(max-width:650px){
    .counter_title{
      width: 50%;
      margin-left:0;
    }
    .counter_items{
      width: 50%;
      margin-right:0;
    }
    .item{
    margin: 10px 0;
    width:8%;
    }
  }
  .number{
    background-color:#6495ed;
    color:white;
    pointer-events:none;
  }
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

