<script>
  import expensesData from "./expenses";
  import List from "./components/List.svelte";
  import { setContext } from "svelte";
  let expenses = [...expensesData];

  const deleteItem = id => {
    console.log("before", expenses);
    expenses = expenses.filter(item => item.id != id);
    console.log("after: ", expenses);
  };
  let state = {
    name1: "simple name",
    handleDeleteItem: deleteItem
  };

  setContext("state", state);
  const deleteEvent = e => {
    console.log(e);
    const { id, name } = e.detail;
    deleteItem(id);
    console.log(name);
  };
</script>

<style>
  nav {
    display: grid;
    height: 200px;
    background-color: greenyellow;
  }
  nav div,
  nav button {
    display: inline;
  }
</style>

<nav>
  <div class="title">Budget calculator</div>
  <button>Add expense</button>
</nav>

<List {expenses} on:delete={deleteEvent} />
<!-- <List {expenses} {deleteItem} /> -->
