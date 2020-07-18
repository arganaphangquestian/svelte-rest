<script>
  let todos = [];
  let todo = "";
  const addTodo = () => {
    if (todo !== "") {
      todos = [...todos, { id: Date.now(), title: todo, isDone: false }];
      todo = "";
    }
  };

  const toggleIsDone = (data) => {
    todos = todos.map((x) => {
      if (x.id === data.id) {
        return {
          ...x,
          isDone: !x.isDone,
        };
      }
      return x;
    });
  };
</script>

<style>
  .container {
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  li.done {
    color: red;
    text-decoration: line-through;
  }
</style>

<!-- Markup -->
<div class="container">
  <form on:submit|preventDefault={addTodo}>
    <input type="text" bind:value={todo} />
    <input type="submit" value="Add Todo" />
  </form>

  <ul>
    {#each todos as x}
      <li on:click={toggleIsDone(x)} class={x.isDone ? 'done' : ''}>
        {x.title} - {x.id}
      </li>
    {/each}
  </ul>
</div>
