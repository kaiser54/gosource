<template>
  <div class="input">
    <label v-if="label">{{ label }}</label>
    <input
      type="text"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    />
  </div>
</template>

<script setup>
defineProps({
  label: {
    type: [String, Boolean],
    default: false,
  },
  modelValue: {
    type: String,
    default: "",
  },
});
</script>

<style>
.input {
  position: relative;
}
.input input {
  display: flex;
  height: 56px;
  padding: 16px;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  gap: 14px;
  flex-shrink: 0;

  color: var(--grey-500);
  font-size: var(--body--small---body--small--regular);

  border-radius: 12px;
  border: 1px solid var(--grey-100);
  background: var(--White);
}
</style>
