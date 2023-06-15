<template>
  <ListHeader/>
  <FormTodo @add="saveTodo"/>
  <TodoList :todos="todos"  @delete-todo="deleteTodo" />
</template>

<script>

import ListHeader from './components/ListHeader';
import TodoList from './components/TodoList';
import FormTodo from './components/FormTodo';

import { ref } from 'vue';
export default {
  name: 'App',
  components: {
    ListHeader,
    TodoList,
    FormTodo,
  }, 
  setup(){

    let todos = ref([]);

    const saveTodo = function (data) {
      // console.log("App template", data);
      todos.value = [...todos.value, {content: data.content, completed: data.completed}];
      // console.log('Array|', todos.value)
    }; 

    const deleteTodo = function (todo){
      // console.log(todos.value[todo].content)
      todos.value.splice(todo, 1);
      // todos.value = todos.value.filter(t => t[index] != t[todo])
    }

    return {
      saveTodo,
      deleteTodo,
      todos,
    }
  }
}

</script>



