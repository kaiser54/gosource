<template>
  <div>
    <DynamicInput v-model="firstName" type="number" class="inputmee" />
    <DynamicButtonNav
      class="nav-button"
      buttonText="click me"
      url="/"
      :isLoading="true"
    />
    <DynamicButtonMain
      class="nav-button"
      buttonText="click me"
      size="large"
      type="primary"
      :isLoading="true"
    />
    <DynamicButtonNav buttonText="click me please" url="" />
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
