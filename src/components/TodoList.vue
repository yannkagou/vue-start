<template>
    <div class="card my-2 item-todo">
        <div  :key="index" v-for="(todo, index) in todos">
            <p @click="toggleTask()" :style="[todo.completed ? {'text-decoration': 'line-through'} : {'text-decoration': 'none'}]">{{ todo.content }}</p>
            <button @click="deleteTodo()">Supprimer</button>
        </div>
    </div>
</template>

<script>

export default {
    emits: ['delete-todo'],
    props: {
        todos: {
            required: true,
        }
    },
    setup(props, {emit}){
        let deleteTodo = function(todo){
            emit("delete-todo", todo);
        };
        const  toggleTask = function(todo){
            console.log(todo);
        };
        return {
            deleteTodo,
            toggleTask
        }
    }
}
</script>

<style>

</style>