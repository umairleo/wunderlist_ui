<template>
  <div>    
    <div class="col-xs-4">
    <h3>Lists</h3>
      <ul class="list-group" v-for="list in lists" :key="list.id">
      <li class="list-group-item">{{ list.name }}</li>
          </ul>
    </div>
  </div>
</template>
<script>

export default {
  name: "ShowLists",
  data() {
    return {
      lists: []
    };
  },
  methods: {
    getAllLists() {
      var headers = {
        headers: {
          token: localStorage.getItem("token")
        }
      };
      this.$http
        .get("http://localhost:3000/lists", headers)
        .then(res => {
          this.lists = res.data;
        })
        .catch(() => {});
    }
  },
  mounted() {
    this.getAllLists();
  }
};
</script>
