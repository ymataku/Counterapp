<script lang="ts">
  import Button from './Button.svelte';
  let titles = ['new'];
  let numbers = [0];
  $: sum = numbers.reduce((sum, element) => sum + element, 0);
  function ButtonEvent(event){
    titles = event.detail.titles;
    numbers = event.detail.numbers;
  }
</script>
<h3>合計:{ sum }</h3>
<Button titles = { titles } numbers = { numbers } on:dispatch={ButtonEvent}/>
<style>
  h3{
    text-align:left;
    font-weight:bold;
    margin:5px;
  }
</style>