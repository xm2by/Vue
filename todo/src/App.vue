<template>
  <div id="app">
    <h1>{{ title }}</h1>
    <TodoInput @newItemInput="getNewItem"/>
    <TodoList :items="items"/>
  </div>
</template>

<script>
import TodoInput from './components/TodoInput';
import TodoList from './components/TodoList';
import Storage from './storage';

export default {
  name: 'App',
  components: {
    TodoInput,
    TodoList
  },
  data () {
    return {
      title: 'Todo',
      items: Storage.fetch()
    }
  },
  watch: {
    items: {
      handler: function(items){
        // console.log(items);
        Storage.save(items);
      },
      deep: true
    }
  },
  methods: {
    getNewItem: function(newItem){
      // console.log(newItem);
      this.items.push({'title': newItem, 'isCompleted': false});
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
