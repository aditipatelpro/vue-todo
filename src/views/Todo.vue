<template lang="pug">
  div
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
              v-btn(icon)
                v-icon mdi-delete

        v-divider

</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  name: 'Home',
  data() {
    return {
      tasks: [
        {
          comment: 'Comment 1',
          done: false,
          id: 'id1',
          title: 'Task 1',
        },
        {
          comment: 'Comment 2',
          done: false,
          id: 'id2',
          title: 'Task 2',
        },
        {
          comment: 'Comment 3',
          done: true,
          id: 'id3',
          title: 'Task 3',
        },
      ],
    };
  },

  methods: {
    handleTaskDone(id:string) {
      const task = this.tasks.filter((x) => x.id === id)[0];
      task.done = !task.done;
    },
  },
});
</script>
