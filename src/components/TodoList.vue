<template>

    <div class="container todo-container">

        <div class="card my-2 item-todo">
            <div  :key="index" v-for="(todo, index) in todos">
                <i class="bi bi-check-lg"></i>
                <p @click="toggleTask(index)" :style="[todo.completed ? {'text-decoration': 'line-through'} : {'text-decoration': 'none'}]">{{ todo.content }}</p>
                <button @click="deleteTodo(index)">Supprimer</button>
            </div>
        </div>

        <form @submit.prevent="addTodo">
            <input v-model="newTodo.content" type="text" placeholder="add a new todo" required>
            <button>Add</button>
        </form>
        
    </div>

</template>

<script>

export default {
    name: 'TodoList',
    data (){
        return {
            todos: [],
            newTodo: {
                content: '',
                completed: false,
            }
        }
    },
    methods: {
        addTodo(){
            this.todos.push(this.newTodo);
            this.newTodo = {
                content: '',
                completed: false,
            }
        },
        deleteTodo(index) {
            this.todos.splice(index, 1);
        },
        toggleTask(index) {
            this.todos[index].completed = !this.todos[index].completed;
        }
    },
    // Sort by completation
    computed: {
    sortedList() {
        let sortedTodos = this.todos;
        sortedTodos = sortedTodos.sort((a,b) => {
            let fa = a.completed.toString(), fb= b.completed.toString();
            if (fa < fb ) {
                return -1;
            }
            if (fa > fb) {
                return 1;
            }
            return 0;
        });
        return sortedTodos; // Ajouter cette ligne pour retourner le tableau trié
    }
}
}

</script>


<style scoped>

/* .todo-container {
        margin-top: 20px;
    } */

</style>