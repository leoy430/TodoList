<template>
    <li>
        <label>
          <input type="checkbox" :checked="todo.done" @change="handleCheck(todo.id)"/>
          <!-- <input type="checkbox" v-model="todo.done"/> -->
          <span>{{todo.thing}}</span>
        </label>
        <button class="btn btn-danger" @click="deleteThing(todo.id)">删除</button>
    </li>
</template>

<script>
    export default({
        name:'MyItem',
        props:['todo','checkTodo','deleteTodo'],
        methods:{
          //勾选or取消勾选
          handleCheck(id){
            this.checkTodo(id)
          },
          //删除
          deleteThing(id){
            if(confirm('确定删除吗')){
              this.deleteTodo(id)
            }
          }
        }
    })
   

  </script>

<style scoped>
    /*item*/
  li {
    list-style: none;
    height: 36px;
    line-height: 36px;
    padding: 0 5px;
    border-bottom: 1px solid #ddd;
  }

  li label {
    float: left;
    cursor: pointer;
  }

  li label li input {
    vertical-align: middle;
    margin-right: 6px;
    position: relative;
    top: -1px;
  }

  li button {
    float: right;
    display: none;
    margin-top: 3px;
  }

  li:before {
    content: initial;
  }

  li:last-child {
    border-bottom: none;
  }

  li:hover{
    background-color: gray;
  }

  li:hover button{
    display: block;
  }
</style>
