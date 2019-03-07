<template>
  <div>
    <button type="button" class="btn btn-danger" @click="logOutUser">
      Log Out
    </button>
  </div>
</template>

<script>
export default {
  name: "LogOut",
  methods: {
    logOutUser() {
      var headers = {
        headers: {
          token: localStorage.getItem("token")
        }
      };
      this.$http
        .delete("http://localhost:3000/sign_out", {}, headers)
        .then(() => {
          localStorage.removeItem("token");
          this.$router.push({ name: "sign_in" });
        })
        .catch(() => {
          localStorage.removeItem("token");
          this.$router.push({ name: "sign_in" });
        });
    }
  }
};
</script>
