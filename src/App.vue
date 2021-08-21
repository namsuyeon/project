<template>
  <div>
    <h1>Todo List</h1>
    <p>제목 : <input type="text" v-model="title"><br>
    내용 : <input type="text" v-model="text"></p>
    <button @click="addTodo"> add </button><br><br>
  </div>
  <div>
    <ul>
      <li v-for="(item,index) in todoList" :key=index>
        <h5>{{item.title}}</h5>
        <p>{{item.text}}</p>
        <button @click="delTodo(index)"> delete </button>
      </li>

    </ul>
  </div>
</template>

<script>

import {pullAt} from 'lodash'

export default {
  name: 'App',
  components: {},
  data() {
    return {
      title : '',
      text : '',
      todoList : [
        
      ]
    }
  },
  methods : {
    addTodo() {
      this.todoList.push({
      title : '> '+ this.title,
      text : ': '+ this.text
      })
    },
    delTodo(index) {
      console.log(index)
      pullAt(this.todoList,[index])
    }
  }
}
</script>

<style scoped>
  div {
    border : solid #1ecad3 1px;
    margin-left : 35%;
    margin-bottom : 10px;
    text-align: center;
    width: 30%;
  
  }
  li {
    
    text-align: left;
    margin-bottom: 2px;
    list-style-type: none;
  }
  button {
    margin: 0px auto;
    width: 80%;
    padding: 5px;
    background-color: #1ecad3;
    font-size : 20px;
    color : #fff;
    
  }
  h1 {
    color: #1ecad3;
  }
  p {
    font-size : 20px;
    color: #17868b;
  }
  input {
    width: 70%;
    padding : 1%;
  }
</style>
