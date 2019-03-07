<template>
  <div>
    <div class="container">
      <div class="row">
        <img alt="Vue logo" src="../assets/logo.png" />
        <div class="pull-right">
          <log-out></log-out>
        </div>
      </div>
      <create-list></create-list> 
    <hr />
      <show-lists></show-lists>
      <task-list></task-list>
    </div>
  </div>
</template>

<script>
import LogOut from "@/components/LogOut.vue";
import CreateList from "@/components/CreateList.vue";
import ShowLists from "@/components/ShowLists.vue";
import TaskList from "@/components/TaskList.vue";
export default {
  name: "home",
  components: {
    LogOut,
    CreateList,
    ShowLists,
    TaskList
  },
  methods: {
    getUser() {
      var token = localStorage.getItem("token");
      if (token === undefined || token === null) {
        this.$router.push({ name: "sign_in" });
      }
    }
  },
  mounted() {
    this.getUser();
  }
};
</script>
