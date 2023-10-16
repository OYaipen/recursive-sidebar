<script setup lang="ts">
import Sidebar from "./components/Sidebar.vue";
import { items } from "./data";

</script>

<template>
  <sidebar :level="1" :items="items" />
</template>

<style scoped></style>
