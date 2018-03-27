<template lang="html">
  <div class="">
    <button type="button" name="button" class="completed-btn" @click="toggleCompleted">completed</button>
    <button type="button" name="button" class="delete-btn" @click="deleteItem">delete</button>
  </div>
</template>

<script>
export default {
  name: 'TodoItemBtn',
  props: ['item'],
  methods: {
    toggleCompleted: function(){
      this.item.isCompleted = !this.item.isCompleted;
      this.$emit('completedStatus', this.item);
    },
    deleteItem: function(){
      this.$emit('isDelete');
    }
  }
}
</script>

<style lang="css">
.completed-btn{
  color: white;
  background: blue;
}
.delete-btn{
  color: white;
  background: red;
}
</style>
