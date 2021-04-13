  
<template>
  <div class="timerBtn">
    
    <div>
      <draggable
        class="list-group"
        tag="ul"
        v-model="todos"
        v-bind="dragOptions"
        @start="isDragging = true"
        @end="isDragging = false"
      >
        <transition-group type="transition" name="flip-list">
          <li
            class="list-group-item"
            v-for="todo in todos"
            :key="todo.id"
          >
      
        <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
            
          </li>
        </transition-group>
      </draggable>
    </div>

    <rawDisplayer class="col-3" :value="list" title="List" />
  </div>
</template>

<script>
import draggable from "vuedraggable";
import Todos from './Todos';
import TodoItem from './TodoItem.vue';
const message = [
  "vue.draggable",
  "draggable",
  "component",
  "for",
  "vue.js 2.0",
  "based",
  "on",
  "Sortablejs"
];
export default {
  name: "transition-example",
  display: "Transition",
  order: 6,
  components: {
    draggable,
    Todos,
    TodoItem,
  },
  props: ['todos'],
  data() {
    return {
      list: message.map((name, index) => {
        return { name, order: index + 1 };
      })
    };
  },
  methods: {
    sort() {
      this.list = this.list.sort((a, b) => a.order - b.order);
    }
  },
  computed: {
    dragOptions() {
      return {
        animation: 0,
        group: "description",
        disabled: false,
        ghostClass: "ghost"
      };
    }
  }
};
</script>

<style>
.button {
  margin-top: 35px;
}
.flip-list-move {
  transition: transform 0.5s;
}
.no-move {
  transition: transform 0s;
}
.ghost {
  opacity: 0.5;
  background: #c8ebfb;
}
.list-group {
  min-height: 20px;
}
.list-group-item {
  cursor: move;
}
.list-group-item i {
  cursor: pointer;
}
.timerBtn{
        display: flex;
        align-items: center;
        justify-content: flex-start;
        width:100%;
    }
</style>