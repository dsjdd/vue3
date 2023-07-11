<template>
  <div id="app">
    <h1>根组件</h1>
  </div>
  <todo-input @addTask="addTask"></todo-input>
  <todo-list :todoList="todoList"></todo-list>
  <todo-button @changeActive="changeActive"></todo-button>

</template>

<script>
import TodoList from './components/todoList.vue'
import todoButton from './components/todoButton.vue'
import todoInput from './components/todoInput.vue'
export default {
  name:'App',
  data(){
    return{
      todoList:[
        {id:1,task:'吃饭',isCompleted:true},
        {id:2,task:'睡觉',isCompleted:false},
        {id:3,task:'打豆豆',isCompleted:false},
      ],
      active:0
    }
    
  },
  computed:{
    todoList(){
      if(this.active===0){
        return this.todoList;
      }
      else if(this.active===1){
        return this.todoList.filter((item)=>item.isCompleted);
      }
      else{
        return this.todoList.filter((item)=>!item.isCompleted);
      }
    }
  },

  methods:{
    changeActive(active){
      this.active=active;
      // console.log(active);
    },
    addTask(taskname){
      this.todoList.push({
        id:this.todoList.length+1,
        task:taskname,
        isCompleted:false,
      })
      

    }
  },
  components:{
    TodoList,
    todoButton,
    todoInput
  }
}
</script>

<style>
</style>
