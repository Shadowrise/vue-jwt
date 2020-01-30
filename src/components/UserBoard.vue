<template>
  <div class="hello">
    <h1>Welcome to regular users page</h1>
    <h2>{{ msg }}</h2>
    <button @click.prevent="logout">Logout</button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      msg: "The commoners"
    };
  },
  methods: {
    logout() {
      this.$http
        .post("http://localhost:3000/logout", {})
        .then(response => {
          debugger;
          localStorage.removeItem("user");
          localStorage.removeItem("jwt");
          console.log("logged out");
          this.$router.push({ name: "login" });
        })
        .catch(function(error) {
          console.error(error.response);
        });
    }
  }
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
