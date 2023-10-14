<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" class="task">

        <h3>{{ task.text }}</h3>
        <p>{{ task.day }}</p>
        <p >{{ task.reminder }}</p>
        <span @click="onDelete(task.id)">X</span>
    </div>
</template>

<script>
    
    export default {
        name: 'Task',
        props: {
            task: Object
        },
        methods: {
            onDelete(id) {
                console.log(id);
                this.$emit('delete-task', id);
            }
        }

    }
</script>