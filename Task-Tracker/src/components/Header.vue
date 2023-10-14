<template>
    <header>
        <h1>{{title}}</h1>
        <Button @btn-click="$emit('btn-click')" text="Add New Task" color="green" />
        <!-- <Button text="Update Task" color="blue" />
        <Button text="Delete Task" color="red" /> -->
    </header>
</template>

<script>
import Button from './Button.vue'
    export default {
        name: 'Header',
        props: {
            title: String
        },
        components: {
            Button
        }

    }
</script>