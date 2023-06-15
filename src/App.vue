<template>
  <ListHeader/>
  <TodoList/>
</template>

<script>

import ListHeader from './components/ListHeader';
import TodoList from './components/TodoList'

export default {
  name: 'App',
  components: {
    ListHeader,
    TodoList
  }
}

</script>



