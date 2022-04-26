<script setup>
  import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <header>
    <div class="wrapper">
      <h1>My Vue Calculator App!</h1>
      <nav>
        <RouterLink active-class="nav-active" class="nav-btn" to="/">Home</RouterLink>
        <RouterLink  active-class="nav-active" class="nav-btn" to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style>
  #app {
    width: 100vw;
  }
  #app h1 {
    width: 100%;
    text-align: center;
  }
  nav {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    width: 100%;
  }
  nav :first-child {
    margin-right: 10px;
  }
  .nav-btn {
    background-color: #40B280;
    width: 75px;
    text-align: center;
    padding: 10px 0 10px 0;
    border-radius: 10px;
    text-decoration: none;
    color: black;
  }
  .nav-btn:hover {
    background-color: #126440;
    cursor: pointer;
  }
  .nav-active {
    background-color: #126440;
  }
</style>
