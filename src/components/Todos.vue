<!--FIRST COMPONENT CREATION -->

<template>
    <div>
        <!-- the props an array so you want to loop through them by using v-for.-->
        <div v-bind:key="todo.id" v-for="todo in todos">
        <!-- you must also set a key by using v-bind:key or else you will get an elint error. -->
        
        <!-- catch the payload from the delete button in todo item component by using v-on -->
            <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
        </div>
    </div>
</template>

<script>
// import the todo item component here
import TodoItem from './TodoItem.vue';

export default {
    name: "Todos",
    // don't forget to add todo item component in export too.
    components: {
        TodoItem
    },
    props: ["todos"]
}
</script>

<style scoped>

</style>