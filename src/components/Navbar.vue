<template>
  <div id="fluid">
    <b-container>
      <a href="#">Home</a>
      <a href="#">Posts</a>
      <a href="#">About</a>
      <a href="#">Contact</a>
      <a href="#" class="float-right">Login</a>
    </b-container>
  </div>
</template>

<script>
export default {
  name: "Navbar"
};
</script>

<style scoped>
#fluid {
  background-color: #2c3e50;
}

#fluid a {
  color: white;
  display: inline-block;
  padding: 15px 10px;
  text-decoration: none;
  transition: all 0.4s ease-in-out;
}

#fluid a:hover {
  color: #46719b;
}
</style>