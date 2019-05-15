<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  let todoText = "";
  function addTodo(e) {
    if (e.type == "keyup" && e.keyCode != 13) {
      return;
    }
    dispatch("addtodo", {
      body: todoText,
      done: false
    });
    todoText = "";
  }
</script>

<style>
  div {
    margin-bottom: 2rem;
  }
  input {
    font-family: inherit;
    padding: 1rem 1.5rem;
  }
</style>

<div>
  <input
    type="text"
    placeholder="What's on your mind ?"
    bind:value={todoText}
    on:keyup={addTodo} />
  <button on:click={addTodo}>Add Todo</button>
</div>
