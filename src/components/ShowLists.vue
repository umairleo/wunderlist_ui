<template>
  <div>    
    <div class="col-xs-4">
    <h3>Lists</h3>
      <ul class="list-group" >
    
      <li class="list-group-item" v-for="list in lists "  :key="list.id" >
        {{ list.name }} {{list.list_id}}<br>
        <a class="button is-primary" @click.submit="addTask()"> Add task    </a> 
       
         <a class="button is-primary" @click="taskList(list)"> Task List
                        </a></li> 
          </ul>

    </div>
  </div>
</template>
<script>

export default {
  name: "ShowLists",
  data() {
    return {
      lists: [],
      task: {

      },
      tasks: []
    };
  },
  methods: {
    taskList(list){
     this.tasks = list.data;
    },
    addTask: function(event){
      event.preventDefault();
     if (this.tasks.name !== '' && this.tasks.name !==undefined){
       this.tasks.push({
         name: this.tasks.name
       })
     }
    },
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
