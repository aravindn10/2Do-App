<template>
  <div class="app">
    <h1>2Do</h1>
    <p class="subtitle">Plan. Prioritize. Perform.</p>

    <div class="input-container">
      <input v-model="newTask" type="text" placeholder="Add your todo" @keyup.enter="addTask" />
      <button @click="addTask">+</button>
    </div>

    <h2>Tasks</h2>
    <ul>
      <li
        v-for="(task, index) in tasks"
        :key="index"
        @dblclick="toggleTask(index)"
        :class="{ done: task.done }"
      >
        {{ task.text }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      newTask: '',
      tasks: []
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push({ text: this.newTask.trim(), done: false });
        this.newTask = '';
      }
    },
    toggleTask(index) {
      this.tasks[index].done = !this.tasks[index].done;
    }
  }
};
</script>