<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput @addTodo="addTodo"></TodoInput>
    <TodoList v-bind:propsdata="todoItems" @removeTodo="removeTodo"></TodoList>
    <TodoFooter @removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script>
  import TodoHeader from './components/TodoHeader.vue'
  import TodoInput from './components/TodoInput.vue'
  import TodoList from './components/TodoList.vue'
  import TodoFooter from './components/TodoFooter.vue'


export default {
  data(){
    return {
      todoItems:[]
    }
  },
    created(){
    if(localStorage.length > 0 ){
      for (var i=0; i<localStorage.length; i++){
        this.todoItems.push(localStorage.key(i));
      }
    }
  },
  methods:{
    addTodo(todoItem){
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    clearAll(){
      localStorage.clear();
      this.todoItems=[];
    },
    removeTodo(todoItem, index){
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
  },
 components:{
   'TodoHeader' : TodoHeader,
   'TodoInput' : TodoInput,
   'TodoList' : TodoList,
   'TodoFooter' : TodoFooter,
 }
}
</script>

<style>
  body { background-color: #f6f6f8;}
  #app {background-color: #fff;box-shadow: 2px 2px 4px rgba(0,0,0,0.15); padding: 10px;
  width: 400px; margin:20px auto; font-family: 'Noto Sans KR', sans-serif;}
</style>
