<template>

    <div class="container todo-container">

        <form @submit.prevent="addTodo">
            <input v-model="newTodo.content" type="text" placeholder="add a new todo" required>
            <button>Add</button>
        </form>
        
    </div>

</template>

<script>

// export default {
//     name: 'FormTodo',
//     data (){
//         return {
//             todos: [],
//             newTodo: {
//                 content: '',
//                 completed: false,
//             }
//         }
//     },
//     methods: {
//         addTodo(){
//             this.todos.push(this.newTodo);
//             this.newTodo = {
//                 content: '',
//                 completed: false,
//             }
//         },
//         deleteTodo(index) {
//             this.todos.splice(index, 1);
//         },
//         toggleTask(index) {
//             this.todos[index].completed = !this.todos[index].completed;
//         }
//     },
//     // Sort by completation
//     computed: {
//     sortedList() {
//         let sortedTodos = this.todos;
//         sortedTodos = sortedTodos.sort((a,b) => {
//             let fa = a.completed.toString(), fb= b.completed.toString();
//             if (fa < fb ) {
//                 return -1;
//             }
//             if (fa > fb) {
//                 return 1;
//             }
//             return 0;
//         });
//         return sortedTodos; // Ajouter cette ligne pour retourner le tableau trié
//     }
// }
// }

import { ref } from 'vue';
export default {
    setup(props, ctx){
        let newTodo = ref({
            content:'',
            completed: false,
        });
        const addTodo = function() {
            // console.log(newTodo.value);
            ctx.emit('add', newTodo.value);
            newTodo.value = {
                content:'',
                completed: false,
            }
        }
        return {
            newTodo,
            addTodo,
        }
    }
}

</script>


<style scoped>

/* .todo-container {
        margin-top: 20px;
    } */

</style>