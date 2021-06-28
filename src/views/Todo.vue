<template lang="pug">
  div
    v-text-field.pa-4(
      append-icon="mdi-plus"
      clearable
      hide-details
      label="Add Task"
      outlined
      v-model="newTaskTitle"
      @click:append="handleAddTask"
      @keyup.enter="handleAddTask"
    )

    v-list(flat)
      div( v-for = "task in tasks" :key="task.id")
        v-list-item(
          :class="{'blue lighten-5': task.done}"
          @click="handleTaskDone(task.id)"
        )
          template(v-slot:default)
            v-list-item-action
              v-checkbox(:input-value="task.done")

            v-list-item-content
              v-list-item-title(:class="{'text-decoration-line-through': task.done}") {{task.title}}
              v-list-item-subtitle {{task.comment}}

            v-list-item-action
              v-btn(icon @click.prevent="handleTaskDelete(task.id)")
                v-icon(color="primary") mdi-delete

        v-divider

</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  name: 'Home',
  data() {
    return {
      newTaskTitle: '',

      tasks: [
        {
          done: false,
          id: 'id1',
          title: 'Task 1',
        },
        {
          done: false,
          id: 'id2',
          title: 'Task 2',
        },
        {
          done: true,
          id: 'id3',
          title: 'Task 3',
        },
      ],
    };
  },

  methods: {

    handleAddTask() {
      const newTask = {
        done: false,
        id: Date.now().toString(),
        title: this.newTaskTitle,
      };
      this.tasks.push(newTask);
      this.newTaskTitle = '';
    },

    handleTaskDelete(id:string) {
      this.tasks = this.tasks.filter((x) => x.id !== id);
    },

    handleTaskDone(id:string) {
      const task = this.tasks.filter((x) => x.id === id)[0];
      task.done = !task.done;
    },

  },
});
</script>
