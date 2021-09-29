<template>
  <div id="app">
    
    <h3>TodoList</h3>
    
    <div>
      <input type="text" name="name" id="name" v-model="text" placeholder="Todoリストの入力...">
      <button @click="addTodo()">追加</button>
    </div>

    <div v-for="(todo, index) in todos" :key="index">
      {{todo.addText}}
      <button @click="removeTodo(index)">削除</button>
    </div>


  </div>
</template>

<script lang='ts'>


//typescript文
interface Member {
  text: string,
  todos: [{
    addText:string
  }]
}
// let addText:string;

import Vue from 'vue';

export default Vue.extend ( {
  data ():Member {
    return {
      text: '',
      todos: [{
        addText:''
      }],
    }
  },

  methods: {
    addTodo():void {
        this.todos.push(
          {
            addText : this.text
          }
        );
        this.text='';
      },

    removeTodo ( index : number ) {
      this.todos.splice( index, 1 );
    },
  }
});
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
