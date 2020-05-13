<template>
    <div>
        <!-- Must traverse to app.vue like delete. No need emit because you want to first construct the todo and then send and then emit. Create method under export default. -->
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
import {v4 as uuidv4} from 'uuid';  // uuid is an id creator.

export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
            // add the v-model in form input after.
        }
    },
    methods: {
        addTodo(e){
            e.preventDefault();
            const newTodo = {
                id: uuidv4(),
                title: this.title,
                completed: false
            }
            //Send up to parent
            this.$emit('add-todo', newTodo);
            //clear title from input bar
            this.title = '';
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }

    input[type="text"]{
        flex: 10;
        padding: 5px;
    }

    input[type="submit"]{
        flex: 2;
    }
</style>