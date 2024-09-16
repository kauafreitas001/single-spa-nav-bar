<template>
  <div id="app">
    <div class="layout">
      <Sidebar />
      <main>
        <router-view />
      </main>
    </div>
  </div>
</template>
<script setup>
import Sidebar from "./components/SideBar.vue";
</script>
<style>
* {
  margin: 0;
  box-sizing: border-box;
  font-family: "Fira sans", sans-serif;
}
.layout {
  display: flex;
}
.main {
  flex: 1;
}
</style>
