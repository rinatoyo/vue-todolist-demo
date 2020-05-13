<!--SECOND COMPONENT CREATION -->

<template>
    <!-- apply the is-complete style by binding class on a condition of if completed. -->
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
        <p>
            <!-- v-on directive is used to add events -->
            <input type="checkbox" v-on:change="markComplete">
            {{todo.title}}
            <!-- to traverse up to the app, emit the event by using @click. (name, parameter). Parameter is sent as a payload-->
            <button @click="$emit('del-todo', todo.id)" class="del">x</button>
        </p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    // define methods used in the input checkbox here
    methods: {
        markComplete(){
            // changes completed status from true to false or vice versa
            this.todo.completed = !this.todo.completed
        }
    }
}
</script>

<style scoped>
    .todo-item {
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }

    .is-complete {
        text-decoration: line-through;
    }

    .del {
        background: #ff0000;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>