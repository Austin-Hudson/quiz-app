<script setup>
import Quiz from "./components/Quiz.vue";

</script>

<template>
  <header class="app-header">Quiz Application</header>
  <main>
    <Quiz title="Quiz 1 - JS Practice" />
  </main>
</template>

<style>
@import "./assets/base.css";

.app-header {
  background-color: #860707;
  color: white;
  padding: 5px;
  cursor: pointer;
}

main {
  display: flex;
  flex-direction: column;
  align-items: center;
}

</style>
