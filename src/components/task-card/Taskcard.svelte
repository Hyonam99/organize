<script>
    import { TaskStore } from "../../store/store"
    import "./taskcard.css";

    export let cardProps

    const handleDelete = (id) => {
        TaskStore.update((tasks) => {
            return tasks.filter(item => item.id !== id)
        })
    }
</script>

<div class="task_card_container">
    <aside>
        <small>{cardProps.priority}</small>
        <h4>{cardProps.title}</h4>
    </aside>
    <div class="task_card_delete-btn">
        <button on:click={() => { handleDelete(cardProps.id)}}>x</button>
    </div>
</div>