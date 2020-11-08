<template>
  <header class="header">
    <h1>Todo List</h1>
    <div id="nav">
      <span><router-link to="/">Home</router-link></span> | 
      <span style="margin-left: 10px"><router-link to="/about">About</router-link></span>
    </div>
  </header>
</template>
<script>
export default {
  name: "Header",
};
</script>
<style scoped>
.header {
  background: #333;
  color: #fff;
  text-align: center;
  padding: 10px;
}
.header a {
  color: #fff;
  padding-right: 5px;
  text-decoration: none;
}
</style>