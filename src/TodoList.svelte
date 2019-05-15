<script>
  import TodoListItem from "./TodoListItem.svelte";
  export let todos = [];
</script>

<style>
  ul {
    list-style-type: none;
    padding: 1rem;
    border: 1px solid #555;
  }
</style>

<h1>Todos</h1>
{#if todos.length > 0}
  <ul>
    {#each todos as todo, i}
      <TodoListItem {todo} index={i} on:tododone on:todoundone on:deletetodo />
    {/each}
  </ul>
{:else}You dont have any todos yet!{/if}
