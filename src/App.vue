<template>
  <div>
    <!-- <img src="./assets/logo.png" alt="logo"> -->
    <MyHeader :receive="receive"/>
    <MyList :todo="todos" :checkTodo="checkTodo" :deleteTodo="deleteTodo"/>
    <MyFooter :todo="todos" :checkAllTodo="checkAllTodo" :clearAllTodo="clearAllTodo"/>
  </div>
</template>

<script>
  import MyHeader from './components/MyHeader.vue';
  import MyList from './components/MyList.vue';
  import MyFooter from './components/MyFooter.vue';

  export default {
      name:'App',
      components:{
        MyHeader,
        MyList,
        MyFooter
      },
      data(){
          return{
              todos:[
              {id:'001',thing:'吃饭','done':true},
              {id:'002',thing:'睡觉','done':false},
              {id:'003',thing:'打豆豆','done':false}]
          }
      },
      methods:{
        receive(todo){
          this.todos.unshift(todo)
        },
        checkTodo(id){
          this.todos.forEach((todo)=>{
            if(id===todo.id) todo.done=!todo.done
          })
        },
        deleteTodo(id){
          this.todos=this.todos.filter(todo=>{
            return todo.id !==id
          })
        },
        checkAllTodo(done){
          this.todos.forEach(todo=>todo.done=done)
        },
        clearAllTodo(){
          this.todos=this.todos.filter((todo)=>{
            return !todo.done
          })
        }
      }
  }
</script>

<style lang="css">
  /*base*/
  body {
    background: #fff;
  }

  .btn {
    display: inline-block;
    padding: 4px 12px;
    margin-bottom: 0;
    font-size: 14px;
    line-height: 20px;
    text-align: center;
    vertical-align: middle;
    cursor: pointer;
    box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
    border-radius: 4px;
  }

  .btn-danger {
    color: #fff;
    background-color: #da4f49;
    border: 1px solid #bd362f;
  }

  .btn-danger:hover {
    color: #fff;
    background-color: #bd362f;
  }

  .btn:focus {
    outline: none;
  }

  .todo-container {
    width: 600px;
    margin: 0 auto;
  }
  .todo-container .todo-wrap {
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
  }
</style>