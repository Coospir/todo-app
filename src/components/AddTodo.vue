<template>
<div>
  <form @submit.prevent="onSubmit">
    <label for="todoText">Add text for your ToDO</label>
    <input id="todoText" class="addTodoInput" type="text" v-model="title">
    <button class="addTodoBtn" type="submit">Create ToDo</button>
  </form>
</div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: ''
    }
  },
  methods: {
    onSubmit() {
      if(this.title.trim()) {
        const newToDo = {
          id: Date.now(),
          title: this.title,
          completed: false
        }
        this.$emit('add-todo', newToDo)
        this.title = null
      }
    }
  }
}
</script>

<style scoped>

  form {
    display: flex;
    align-items: center;
    align-content: center;
    justify-content: center;
  }
  .addTodoInput {
    border: 1px solid #c3c3c3;
    margin: 15px;
    width: 300px;
  }

  .addTodoBtn {
    border-radius: 5px;
    background: green;
    color: #fff;
    border: 0;
    padding: 5px;
    font-size: 10px;
  }

  label {
    font-size: 12px;
    color: #c3c3c3;
  }
</style>