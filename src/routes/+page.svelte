<script>

import './app.css'

/**
 * @typedef {{title: string; done: boolean}} Task
 */

 /** @type {Task[]}*/
let tasks = $state([])
let task = $state('')   

const handleAddTask = () => {
    tasks = [...tasks, {title: task, done: false}]
    task = ''
}

/**
 * @param {number} index
 */
const remoteTask = (index) => {
    tasks = tasks.filter((_, i) => i !== index)
}
</script>

<main class="container">

    <h1>Tasks</h1>

    <input bind:value={task} />
    <button on:click={handleAddTask}>Add Task</button>

    <ul class="tasks">
        {#each tasks as task, index}
            <li class="task">
                <small>{task.title}</small>
                <button on:click={() => remoteTask(index)}>Remove</button>
            </li>
        {/each}
    </ul>
</main>


<style>

.container {
    height: 100vh;
    box-shadow: var(--shadow-1);
}

.tasks {
    box-shadow: var(--shadow-2);
    padding: var(--size-3); 
    list-style: none;
}

header {
  background-image: var(--gradient-5);

  @media (--OSdark) {
    background-image: var(--gradient-15);
  }
}

</style>
