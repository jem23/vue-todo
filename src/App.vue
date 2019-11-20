
// HTML part 
<template>
  <div id="app">
    <div class="todo-wrapper">
      <div class="todo-container">
        <!-- <TodoLIst />  -->
          <todo-list :todos="todos"/>
          <div class="todo-create-btn-container"> 
            <todo-create @formSubmitted="createTodo"/>
          </div>
      </div>
    </div>
    
  </div>
</template>

<script>

import playground from './playground'
import TodoList from '@/components/TodoList'
import TodoCreate from '@/components/TodoCreate'
import store from '@/store'
export default {
  name: 'app',
  components: {
    TodoList, TodoCreate
  },
  data(){
    return {
      todos: store.state.todos
    }
  },
  //this function is run automatically by vue framework
  created() {
    //playground()
    this.todos = store.dispatch('initStore')
  },
  methods: {
    createTodo(todo) {
        
        store.dispatch('createTodo', todo)
      }  
  }
  
  
}

</script>

<style lang="scss">

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

.app-error {
  color: #ff1212;
}

.app-form {
    .label {
        display: block;
        font-size: 18px;
        font-weight: bold;
    }

    .form-input {
        padding: 10px;
        font-size: 17px;
        width: 80%;
        

    }

    .form-control {
        margin-bottom: 10px;

        &-last {
          margin-bottom: 0px;
        }
    }
}

.app-button {
  font-size: 20px;
  padding: 10px;
  border-radius: 5px;
  background-color: #795899;
  color: white;
  font-weight: bold;

  &:hover {
    cursor: pointer;
  }
}

.is-primary {
  background-color: #47ca47 !important;

}

.is-warning {
  background-color: #ffa753 !important;
}

.is-danger {
  background-color: #ff5a5a !important;
}



.todo {
  &-wrapper {
      /*flexible styling */
  display: flex;
  /* it defines alignment along the main axis */
  justify-content: center;
  
  width: 100%;
  }

    &-create-btn-container {
      margin: 10px;
    }

  &-container {
      display: flex;
      flex-direction: column;
      width: 400px;
      min-height: 200px;
      background-color: #ededed;
      border-radius: 5px;

  }
  
}

</style>
