<template lang="html">
  <input placeholder="Add New Todo Item" v-model="newItem" @keyup.enter="addNewItem(newItem)">
</template>

<script>
export default {
  data () {
    return {
      newItem: ''
    }
  },
  methods: {
    addNewItem: function(newItem){
      // console.log(this.newItem);
      this.$emit('newItemInput', this.newItem);
      this.newItem = '';
    }
  }
}
</script>

<style lang="css">
</style>
