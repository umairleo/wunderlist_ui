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
      <show-lists>
        <add-task></add-task>
      </show-lists>
    
    </div>
  </div>
</template>

<script>
import LogOut from "@/components/LogOut.vue";
import CreateList from "@/components/CreateList.vue";
import ShowLists from "@/components/ShowLists.vue";
import AddTask from "@/components/AddTask.vue";
export default {
  name: "home",
  components: {
    LogOut,
    CreateList,
    ShowLists,
    AddTask
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
