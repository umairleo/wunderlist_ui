<template >
<div class="col-xs-8">
<h3>Tasks</h3>
<ul class="list-group" v-for="task in tasks" :key="task.list_id" >{{list.id}}
<li class="list-group-item">{{ task.name }}</li>
</ul>
</div>
</template>

<script>
export default {
  name: "TaskList",
  data() {
    return {
      tasks: []
    };
  },
  methods: {
    getAllTasks() {
      var headers = {
        headers: {
          token: localStorage.getItem("token")
        }
      };
      this.$http
        .get("http://localhost:3000/lists/:list_id/tasks",{}, headers)
        .then(res => {
          console.log(res);
       this.tasks = res.data;
        })
        .catch(() => {});
    }
  },
  mounted() {
    this.getAllTasks();
  }
};
</script>

<style></style>
