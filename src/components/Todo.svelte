<script>
  export let dataTodo;
  export let onToggle;
  export let onDelete;
</script>

<style>
  li.done {
    color: red;
    text-decoration: line-through;
  }
</style>

<!-- Markup -->
<li class={dataTodo.isDone ? 'done' : ''}>
  <input
    type="checkbox"
    checked={dataTodo.isDone}
    on:change={onToggle(dataTodo)} />
  {dataTodo.title} - {dataTodo.id}
  <button on:click={onDelete(dataTodo)}>X</button>
</li>
