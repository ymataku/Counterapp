<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();
	function add() {
		dispatch('new', {
			text: "new",
			number:0
		});
  }
</script>

<button class="add" on:click={ add }>new</button>

<style>
.add{
      width:100%;
      margin-top:20px;
      background-color:#dcdcdc;
  }
  .add:hover{
      background-color:#ffffff;
  }
</style>

