<template>
  <div>
    <ul>
      <TodoItem v-for="(item, i) in list" :key="item.id" v-bind:item="item" v-on:removeItem="removeItem" v-bind:index="i"/>
    </ul>
  </div>
</template>

<script>
import TodoItem from "@/components/TodoItem";
export default {
  props: ['list'],
  name: "TodoList",
  components: {TodoItem},
  methods: {
    removeItem(id) {
      this.$emit('removeItem', id)
    }
  }
}
</script>

<style scoped>
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }
</style>