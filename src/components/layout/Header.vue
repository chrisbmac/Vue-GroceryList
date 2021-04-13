<template>
  <header class="header">
    <h1>Shopping List <b-icon icon="basket"></b-icon></h1>
    <div id="nav">
      <b-button-group>
        <b-button variant="outline-primary">
          <router-link to="/">Home
            <b-icon icon="home"></b-icon>
          </router-link>
        </b-button>
        <b-button variant="outline-primary">
          <router-link to="/about">About<b-icon icon="about"></b-icon>
          </router-link>
        </b-button>
      </b-button-group>
    </div>
    <hr>
  </header>
</template>

<script>
export default {
  name: "Header"
}
</script>

<style scoped>
  .header {
    background: rgb(255, 255, 255);
    color: rgb(29, 53, 236);
    text-align: center;
    padding: 10px;
  }

  .header a {
    color: rgb(10, 10, 10);
    padding-right: 5px;
    text-decoration: none;
  }
</style>


