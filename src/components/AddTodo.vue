<template>
  <div class="timerBtn">
    <form @submit.prevent="addTodo">
      <b-input-group>
        <b-input-group-prepend is-text>
          <b-icon icon="basket"></b-icon>
          <b-form-input type="text" v-model="title" name="title" placeholder="Add item"></b-form-input>
        </b-input-group-prepend>
        <b-button type="submit" variant="outline-primary">
          <b-icon icon="bag-plus"></b-icon>
        </b-button>
      </b-input-group>
    </form>
  </div>
</template>

<script>
// import uuid from 'uuid';
export default {
  name: "AddTodo",
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo() {
      const newTodo = {
        title: this.title,
        completed: false
      }
      // Send up to parent
      this.$emit('add-todo', newTodo);

      this.title = '';
    }
  }
}
</script>

<style scoped>
  form {
    display: flex;
  }

  .timerBtn{
        display: flex;
        align-items: center;
        justify-content: flex-start;
        width:100%;
        margin: 2%;
        
    }
</style>


