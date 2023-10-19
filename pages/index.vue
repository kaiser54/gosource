<template>
  <div>
    <DynamicInput v-model="firstName" type="number" class="inputmee" />
    <p>{{ firstName }}</p>
  </div>
</template>

<script setup>
import { ref } from "vue";

const firstName = ref("");
</script>
