<script>
  import Item from "./Item.svelte";

  export let expenses;
  //   export let deleteItem;
</script>

<style>
  /* your styles go here */
</style>

<div class="expenses">
  {#each expenses as item, index}
    <!-- <Item {...item} index={index + 1} {deleteItem} /> -->
    <Item {...item} on:delete />
  {/each}
</div>
