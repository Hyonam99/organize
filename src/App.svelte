<script>
	import Taskcard from "./components/task-card/Taskcard.svelte";
	import TaskInput from "./components/task-input/TaskInput.svelte";
	import { TaskStore } from "./store/store"

  $: totalTask = $TaskStore.length
  $: urgentTasks = $TaskStore.filter(item => item.priority === "urgent").length
</script>

<main>
	<h1>Organize !</h1>

	<section class="organize_header">
		<p>Total tasks: {totalTask}</p>
		<p>Urgent tasks: {urgentTasks}</p>
	</section>

	<section>
		<TaskInput />
	</section>

	<section class="organize_task-cards">
		{#each $TaskStore as task (task.id)}
			<Taskcard cardProps={task} />
		{/each}
	</section>
</main>
