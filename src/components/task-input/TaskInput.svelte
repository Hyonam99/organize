<script>
    import { TaskStore } from "../../store/store"
    import TaskPriority from "../task-priority/TaskPriority.svelte";
    import { faker } from "@faker-js/faker"
    import "./task-input.css"
    let title = ""
    let desc = ""
    let priority = ""

    const resetForm = () => {
        title = ""
        desc = ""
        priority = ""
    }

    const handleSubmit = () => {
        const newTask = {id: faker.string.uuid(), title, desc, priority}
        TaskStore.update((tasks) => {
            return [newTask, ...tasks]

        })
        resetForm()
    }

    const handleSelected = (e) => {
        priority = e.detail
    }
</script>

<div class="task_input_container">
    <form on:submit|preventDefault={handleSubmit}>
        <label for="title">
            Title:
            <input type="text" name="title" id="title" bind:value={title}/>
        </label>

        <label for="desc">
            Description: 
            <textarea name="desc" id="desc" rows="4" bind:value={desc}/>
        </label>

        <TaskPriority on:select-priority={handleSelected} {priority}/>

        <button type="submit">save</button>
    </form>
</div>
