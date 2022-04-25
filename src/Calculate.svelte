<script lang="ts">
  import AddToList from './AddToList.svelte';
  import Increment from './Increment.svelte';
  import Decrement from './Decrement.svelte';
  import ResetNumber from './ResetNumber.svelte';
  import RemoveFromList from './RemoveFromList.svelte';
  let title = ['new']
  let num = [0]
  
  $: sum = num.reduce((sum, element) => sum + element, 0)
  
  function EventHandler(event) {
    let index = event.detail.index
    switch(event.type){
      case "new":
        title = [...title,event.detail.text]
        num = [...num,event.detail.number]
        break;
      case "increment":
        num[index] += 1;
        break;
      case "decrement":
        num[index] -= 1;
        break;
      case "reset":
        num[index] = 0;
        break;
      case "remove":
        num.splice(index, 1);
        title.splice(index, 1);
        num = num;
        title = title;
        break;
      default:
        console.log("default");
        break;
    }
  }
</script>
<p>合計:{ sum }</p>
{#each title as title, index}
  <div class="counter">
    <input class="counter_title" placeholder= { title }  bind:value = { title } >
    <span class="counter_items">
      <button class="item number">{ num[index] }</button>
      <Increment index = { index } on:increment={ EventHandler }/>
      <Decrement index = { index } on:decrement={ EventHandler }/>
      <ResetNumber index = { index } on:reset={ EventHandler }/>
      <RemoveFromList index = { index } on:remove={ EventHandler }/>
    </span>
    
  </div>
{/each} 
<AddToList on:new={ EventHandler }/>

<p>titl:{title}</p>

<style>
  p{
    text-align:left
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
  }
  .counter_items{
    width: 40%;
    margin-right:0;
    }
  .number{
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
    .item {
      margin: 10px 0;
      width:8%;
    }
  }
</style>