<template>
  <div>
    <h1 class="text-center">Sign Up Page</h1>
    <div class="container">
      <div class="row">
        <div class="col-md-6 col-md-offset-3">
          <form @submit.prevent="submitForm">
            <div
              class="alert alert-danger"
              role="alert"
              v-if="formErrors.length > 0"
            >
              <ul>
                <li v-for="error in formErrors">{{ error }}</li>
              </ul>
            </div>
            <div class="form-group">
              <label for="name">Name</label>
              <input
                type="text"
                class="form-control"
                id="name"
                placeholder="Name"
                v-model="formData.name"
              />
            </div>
            <div class="form-group">
              <label for="username">Username</label>
              <input
                type="text"
                class="form-control"
                id="username"
                placeholder="Username"
                v-model="formData.username"
              />
            </div>
            <div class="form-group">
              <label for="exampleInputEmail1">Email address</label>
              <input
                type="email"
                class="form-control"
                id="exampleInputEmail1"
                placeholder="Email"
                v-model="formData.email"
              />
            </div>
            <div class="form-group">
              <label for="exampleInputPassword1">Password</label>
              <input
                type="password"
                class="form-control"
                id="exampleInputPassword1"
                placeholder="Password"
                v-model="formData.password"
              />
            </div>
            <div class="form-group">
              <label for="bio">Bio</label>
              <input
                type="text"
                class="form-control"
                id="bio"
                placeholder="Bio"
                v-model="formData.bio"
              />
            </div>
            <button type="submit" class="btn btn-default">Submit</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SignUp",
  data() {
    return {
      formData: {},
      formErrors: []
    };
  },
  methods: {
    submitForm() {
      this.$http
        .post("http://localhost:3000/sign_up", this.formData)
        .then(() => {
          this.formData = {};
          this.$router.push({ name: "sign_in" });
        })
        .catch(error => {
          this.formErrors = error.response.data.errors;
        });
    }
  }
};
</script>
