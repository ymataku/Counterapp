<script lang="ts">
  import AddToList from './AddToList.svelte';
  let title = ['new']
  let num = [0]
  
  $: sum = num.reduce((sum, element) => sum + element,0)
  function removeFromList(i:number) {
    num.splice(i, 1)
    title.splice(i, 1)
    num = num
    title = title
  }
  
  function resetIndex(i:number) {
		num[i] = 0
  }

  function Increment(i:number){
      num[i] += 1 
      
  }

  function Decrement(i:number){
    if(num[i] > 0){
      num[i] -= 1
    }else{
      return
    }
  }

  function test(event) {
    if(event.type == "new"){
      title = [...title,event.detail.text]
      num = [...num,event.detail.number]
    }
  }
  
</script>
<p>合計:{ sum }</p>
{#each title as title, index}
  <div class="counter">
    <input class="counter_title" placeholder= { title }  bind:value = { title } >
    <span class="counter_items">
      <button class="item number">{ num[index] }</button>
      <button class="item" on:click={() => Increment(index)}>+</button>
      <button class="item" on:click={() => Decrement(index)}>-</button>
      <button class="item" on:click={() => resetIndex(index)}>0</button>
      <button class="item" on:click={() => removeFromList(index)}>×</button>
    </span>
    
  </div>
{/each} 
<AddToList on:new={ test }/>

<p>{title}</p>

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
  .item{
    margin: 10px 0;
    width:40px;

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