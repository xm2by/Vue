<template lang="html">
    <ul>
      <li v-for="(item, index) in items">
        <div :class="{completed: item.isCompleted}">{{ item.title }}</div>
        <TodoItemBtn :item="item"  @completedStatus="getItemCompletedStatus" @isDelete="deleteItem(index)"/>
      </li>
    </ul>
</template>

<script>
import TodoItemBtn from './TodoItemBtn';

export default {
  name: 'TodoList',
  components: {
    TodoItemBtn
  },
  props: ['items'],
  data () {
    return {
      isDelete: false
    }
  },
  methods: {
    getItemCompletedStatus: function(item){
      this.item = item;
    },
    deleteItem: function(index){
      this.items.splice(index, 1);
    }
  }
}
</script>

<style lang="css">
.completed{
  font-weight: bold;
  color: green;
  text-decoration: underline;
}
</style>
