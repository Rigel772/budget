<script>
  import Title from "./Title.svelte";
  import { getContext, createEventDispatcher } from "svelte";
  //   export let expense;
  //   let { name, amount, id } = expense;
  let state;
  const { handleDeleteItem, name1 } = getContext("state");
  export let id;
  export let name;
  export let amount;

  const dispatch = createEventDispatcher();

  let showAmount = false;
  //   console.log("from item: ", expense);
</script>

<style>
  /* your styles go here */
</style>

<div class="card" on:click={() => (showAmount = !showAmount)}>
  <Title content="{name1}. {name}" />
  {#if showAmount}
    <p>{amount}</p>
  {/if}

</div>
<button on:click={dispatch('delete', { id, name: 'Oskar' })}>
  <!-- <button on:click={handleDeleteItem(id)}> -->
  <!-- <button on:click={() => deleteItem(id)}> -->
  <i class="material-icons">android</i>
  Delete
</button>
