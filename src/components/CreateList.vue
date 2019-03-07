<template>
  <div >
     <form class="form-horizontal" action="#" @submit.prevent="submitform">
<label for="name">Create New List</label>
            <div class="input-group">
              
             <input type="text" class="form-control" id="name" placeholder="Enter New List"
          v-model="formData.name">
             <span class="input-group-btn">
                  <button class="btn btn-success" type="submit">Submit</button>
             </span>
          </div>
          </form>
  </div>
</template>

<script>
export default {
  name: "CreateList",
  data() {
    return {
      formData: {}
    };
  },
  methods: {
    submitform() {
      var headers = {
        headers: {
          token: localStorage.getItem("token")
        }
      };
      this.$http
        .post("http://localhost:3000/lists", this.formData, headers)
        .then(() => {
          this.formData = {};
        })
        .catch(() => {});
    }
  }
};
</script>
