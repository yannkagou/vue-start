<template>
  <ListHeader/>
  <FormTodo @add="saveTodo"/>
  <div class="card my-2 item-todo">
        <div  :key="index" v-for="(todo, index) in todos">
            <p @click="toggleTask(index)" :style="[todo.completed ? {'text-decoration': 'line-through'} : {'text-decoration': 'none'}]">{{ todo.content }}</p>
            <button @click="deleteTodo(index)">Supprimer</button>
        </div>
     </div>
</template>

<script>

import ListHeader from './components/ListHeader';
import FormTodo from './components/FormTodo';

import { ref } from 'vue';
export default {
  name: 'App',
  components: {
    ListHeader,
    FormTodo,
  }, 
  setup(){

    let todos = ref([]);

    const saveTodo = function (data) {
      todos.value = [...todos.value, {content: data.content, completed: data.completed}];
    }; 

    const deleteTodo = function (todo){
      // console.log(todos.value[todo].content)
      todos.value.splice(todo, 1);
    };

    const toggleTask = function (todo){
      todos.value[todo].completed = !todos.value[todo].completed;
    }
    return {
      saveTodo,
      deleteTodo,
      toggleTask,
      todos,
    }
  }
}

</script>



