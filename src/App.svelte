<script>
  import { onMount } from "svelte";
  import Header from "./Header.svelte";
  import TodoInput from "./TodoInput.svelte";
  import TodoList from "./TodoList.svelte";
  let todos = [];
  onMount(() => {
    const fetchedTodos = JSON.parse(window.localStorage.getItem("todos"));
    todos = fetchedTodos || [];
  });
  function addTodo(event) {
    // todos.push(event.detail);
    todos = [...todos, event.detail];
    cacheTodos();
  }
  function handleTodoDone(event) {
    todos[event.detail.index].done = true;
    cacheTodos();
    // todos = [...todos];
  }
  function handleTodoUndone(event) {
    todos[event.detail.index].done = false;
    cacheTodos();
    // todos = [...todos];
  }
  function handleTodoDelete(event) {
    todos.splice(event.detail.index, 1);
    todos = [...todos];
    cacheTodos();
  }
  function cacheTodos() {
    window.localStorage.setItem("todos", JSON.stringify(todos));
  }
</script>

<style>

</style>

<Header />
<TodoInput on:addtodo={addTodo} />
<TodoList
  {todos}
  on:tododone={handleTodoDone}
  on:todoundone={handleTodoUndone}
  on:deletetodo={handleTodoDelete} />
