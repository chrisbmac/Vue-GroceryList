<template>
  <div>
    <div class="timerBtn">
      <form @submit.prevent="addTodo">
        <b-input-group >
          <b-input-group-prepend is-text>
            <b-form-input type="text" v-model="title" name="title" placeholder="Add item"></b-form-input>
          </b-input-group-prepend>
          <b-button type="submit" variant="outline-primary">
            <b-icon icon="bag-plus"></b-icon>
          </b-button>
        </b-input-group>
      </form>
    </div>
    <div v-if="error" class="timerBtn">
      <span class="text-danger"><b-icon icon="emoji-frown-fill" animation="throb"></b-icon>{{error}}<b-icon icon="emoji-frown-fill" animation="spin-reverse"></b-icon></span>
    </div>
  </div>
</template>

<script>
// import uuid from 'uuid';
export default {
  name: "AddTodo",
  data() {
    return {
      title: '',
      error: '',
    }
  },
  methods: {
    addTodo() {
      if(!this.title) return this.error = "You must provide an actual item! Come on man..";
      const newTodo = {
        title: this.title,
        completed: false
      }
      // Send up to parent
      this.$emit('add-todo', newTodo);
      this.error = '';
      this.title = '';
    }
  }
}
</script>

<style scoped>
  .timerBtn{
        display: flex;
        align-items: center;
        justify-content: center;
        width:100%;
        margin: 2%;
    }
</style>


