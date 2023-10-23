<template>
  <div>
    <DynamicInput v-model="firstName" type="number" class="inputmee" />
    <DynamicNavButton class="nav-button" buttonText="click me" url="/" />
    <DynamicNavButton buttonText="click me please" url="" />
    <p>{{ firstName }}</p>
    <Account name="Agboola t." />
  </div>
</template>

<script setup>
import { ref } from "vue";

const firstName = ref("");
</script>

<style scoped>
</style>
