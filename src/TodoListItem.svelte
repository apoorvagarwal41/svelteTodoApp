<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let todo, index;
  function doneTodo() {
    if (todo.done) {
      dispatch("todoundone", {
        index
      });
      return;
    }
    dispatch("tododone", {
      index
    });
  }
  function deleteTodo(e) {
    e.stopPropagation();
    dispatch("deletetodo", {
      index
    });
  }
</script>

<style>
  li {
    cursor: pointer;
    padding: 10px;
    border-bottom: 1px solid #555;
    display: flex;
    justify-content: space-between;
  }
  li.done span {
    color: #444;
    opacity: 0.6;
  }
</style>

<li on:click={doneTodo} class={todo.done ? 'done' : ''}>
  <span>{todo.body}</span>
  <button on:click={deleteTodo}>Delete</button>
</li>
