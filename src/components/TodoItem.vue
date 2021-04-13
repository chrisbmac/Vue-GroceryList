<template>
  <b-form-group size="sm">
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
      <p>
        <input type="checkbox" v-on:change="markComplete" v-bind:checked="todo.completed">
        {{todo.title}}
        <b-button variant="danger" class="del" @click="$emit('del-todo', todo.id)">
          <b-icon icon="bag-x"></b-icon>
        </b-button>
      </p>
    </div>
  </b-form-group>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
}
</script>

<style scoped>
  .todo-item {
    background: #2e5bf0;
    padding: 10px;
    border-radius: 2%;
    border-bottom: 1px rgb(2, 2, 2) dotted;
  }

  .is-complete {
    text-decoration: line-through;
    background-color: rgb(81, 236, 81);
  }

  .del {
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>

