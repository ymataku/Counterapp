<script lang="ts">
  import { counts } from "./stores.js";

  let sum:number = 0;
  for(let key in $counts){
    sum += $counts[key].num; 
  }
  
  function removeFromList(i:number) {
    sum -=  $counts[i].num
    $counts.splice(i, 1)
    $counts = $counts
  }
  
  function resetIndex(i:number) {
    sum -=  $counts[i].num
		$counts[i].num = 0
  }

  function Increment(i:number){
      sum += 1
      $counts[i].num += 1 
      console.log($counts[i].num)
  }

  function Decrement(i:number){
    if($counts[i].num > 0){
      sum -=  1
      $counts[i].num -= 1
    }else{
      return
    }
  }

  function addToList() {
    $counts = [...$counts, {title: "new", num: 0}]
  }
</script>
<p>合計：{ sum }</p>
{#each $counts as count, index}
  <div class="count">
    <input type="text" placeholder="{count.title}" />
    <span class="calam">
      <button class="item">{count.num}</button>
      <button class="item" on:click={() => Increment(index)}>+</button>
      <button class="item" on:click={() => Decrement(index)}>-</button>
      <button class="item" on:click={() => resetIndex(index)}>0</button>
      <button class="item" on:click={() => removeFromList(index)}>×</button>
    </span>
  </div>
{/each} 
<button class="new" on:click={addToList}>new</button>

<style>
  p{
    text-align:left
  }
  .count{
    margin-top:5px;
    width:100%;
    margin:5px auto;
    box-shadow: 2px 2px 4px;
  }
  .calam{
    width: 50%;
    margin-right:0;
    
    }
  .item{
    margin: 10px 0;
    width:40px;
  }
  input{
    width: 60%;
    margin-left:0;
  }
  .new {
      width:100%;
      margin-top:20px;
  }
</style>