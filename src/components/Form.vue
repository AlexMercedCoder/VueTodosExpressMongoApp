<template>
<div>
<form @submit="handleSubmit">
    <input type=text v-model="reminder">
    <input type=checkbox v-model="completed">
    <input type=submit value=submit>
</form>
</div>
</template>

<script setup>
import {ref, defineProps} from "vue"

const reminder = ref(props.reminder)
const completed = ref(props.completed)
const _id = ref(props._id)
const action = ref(props.action)
const props = defineProps({
    reminder: String,
    completed: Boolean,
    _id: String,
    action: String,
    createTodo: Function,
    updateTodo: Function
})

const handleSubmit = () => {
    if (action.value === "create"){
        const todo = {reminder: reminder.value, completed: completed.value}
        props.createTodo(todo)
    }
    if (action.value === "update"){
        const todo = {reminder: reminder.value, completed: completed.value, _id: _id.value}
        props.updateTodo(todo)
    }
}




</script>

<style>

</style>