<template>
<li>
  <span v-bind:class="{completed: item.completed}">
    <input class="flagCompleted" type="checkbox" v-on:change="item.completed = !item.completed">
    <strong>{{index + 1}}</strong>
    {{item.title}}
  </span>
  <button class="deleteItem" v-on:click="$emit('removeItem', item.id)">&times;</button>
</li>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true
    },
    index: Number
  },
  name: "TodoItem"
}
</script>

<style scoped>
  li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px;
    margin: 15px;
    border: 1px solid #ccc;
  }

  .deleteItem {
    font-weight: 900;
    border-radius: 5px;
    background: red;
    color: #fff;
    border: 0;
  }

  .flagCompleted {
    margin-right: 15px;
  }

  .completed {
    text-decoration: line-through;
  }
</style>