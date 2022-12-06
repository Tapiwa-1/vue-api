<script setup>
import { RouterLink, RouterView } from "vue-router";
import Nav from "./components/Nav.vue";
</script>

<template>
  <Nav/>
  <main class="max-w-7xl mx-auto min-h-screen">
    <RouterView />
  </main>
</template>
