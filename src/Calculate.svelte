<script lang="ts">
  import AddToList from './AddToList.svelte';
  import Increment from './Increment.svelte';
  import Decrement from './Decrement.svelte';
  import ResetNumber from './ResetNumber.svelte';
  import RemoveFromList from './RemoveFromList.svelte';

  let titles = ['new'];
  let numbers = [0];
  $: sum = numbers.reduce((sum, element) => sum + element, 0);

  function CalculationtHandler(event) {
    numbers = event.detail.numbers;
    titles = event.detail.titles;
  }
</script>
<h3>合計:{ sum }</h3>
{#each titles as title, index}
  <div class="counter">
    <input class="counter_title" bind:value = { title } >
    <span class="counter_items">
      <button class="number">{ numbers[index] }</button>
      <Increment index = { index } titles = { titles }  numbers = { numbers } on:increment={ CalculationtHandler }/>
      <Decrement index = { index } titles = { titles } numbers = {numbers} on:decrement={ CalculationtHandler }/>
      <ResetNumber index = { index } titles = { titles } numbers = {numbers} on:reset={ CalculationtHandler }/>
      <RemoveFromList index = { index } titles = { titles } numbers = {numbers} on:remove={ CalculationtHandler }/>
    </span>
  </div>
{/each} 
<AddToList titles = { titles } numbers = {numbers} on:new={ CalculationtHandler }/>
<h3>title: { titles }</h3>
<style>
  h3{
    text-align:left;
    font-weight:bold;
    margin:5px;
  }
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
  .number{
    margin: 10px 0;
    width:40px;
    border: none;
    background-color:#6495ed;
    color:white;
    pointer-events:none;
  }
  
  @media(max-width:650px){
    .counter_title {
      width: 50%;
      margin-left:0;
    }
    .counter_items {
      width: 50%;
      margin-right:0;
    }
  }
</style>