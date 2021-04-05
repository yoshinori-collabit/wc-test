<template>
  <div>
    <form>
      {{ msg }}
      <div>
        <label for="new_title">タイトル</label>
        <input type="text" id="new_title" v-model="newTask.title" />
      </div>
      <div>
        <label for="new_body">本文</label>
        <input type="text" id="new_body" v-model="newTask.body" />
      </div>

      <button type="submit" @click.prevent="addTask">追加する</button>
    </form>

    <div v-for="task in tasks" :key="task.id">
      <h2>
        {{ task.title }}
      </h2>
      <p>{{ task.body }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
    initTasks: {
      type: Array,
      default: () => [{ id: 1, title: "帰る", body: "aaaaaaaaaa" }],
    },
  },
  data() {
    return {
      tasks: this.initTasks,
      newTask: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    resetForm() {
      this.newTask = {
        title: "",
        body: "",
      };
    },
    addTask() {
      this.tasks = [...this.tasks, this.newTask];
      this.$emit("eventName", this.tasks);
      console.log("emited");
      this.resetForm();
    },
  },
};
</script>
