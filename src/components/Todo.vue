/* eslint-disable prettier/prettier */ /* eslint-disable prettier/prettier */
<template>
  <div class="container">
    <h1 class="text-center mt-5">Todo list app</h1>
    <div class="d-flex">
      <input
        v-model="task"
        type="text"
        placeholder="Enter text here"
        class="form-control"
      />
      <button @click="submit()" class="btn btn-primary rounded-0">
        Submit
      </button>
    </div>
    <!-- list -->
    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th scope="col">Task</th>
          <th scope="col">Status</th>
          <th scope="col">#</th>
          <th scope="col">#</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <th scope="row">{{ task.name }}</th>
          <td>{{ task.status }}</td>
          <td>
            <div class="text-center" @click="updateTask(index)">
              <span class="fa fa-pen"></span>
            </div>
          </td>
          <td>
            <div class="text-center" @click="deleteTask(index)">
              <span class="fa fa-trash"></span>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script lang="js">
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      task: "",
      updatedTask: null,
      tasks: [
        {
          name: "Buy milk",
          status: "to-do",
        },
        {
          name: "Buy bread",
          status: "in-progress",
        },
      ],
    };
  },
  methods: {
    submit() {
      if (this.task.length === 0) return;
      if(this.updatedTask === null){
        this.tasks.push({
            name: this.task,
            status: "to-do"
        });
      }else{
          this.tasks[this.updatedTask].name == this.task;
          this.updatedTask = null;
      }
      this.task = "";
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    updateTask(index){
        this.task = this.tasks[index].name;
        this.updatedTask = index;
    }
  },
};
</script>

<style scoped></style>
