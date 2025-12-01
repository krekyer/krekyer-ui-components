<template>
  <select
    :class="$style.select"
    :value="modelValue"
    @change="
      $emit('update:modelValue', ($event.target as HTMLSelectElement).value)
    "
    :disabled="isDisabled"
    :data-disabled="isDisabled"
  >
    <option v-for="option in options" :key="option" :value="option">
      {{ option }}
    </option>
  </select>
</template>

<script setup lang="ts">
defineProps<{
  modelValue: string;
  isDisabled?: boolean;
  options: string[];
}>();

defineEmits<(e: 'update:modelValue', value: string) => void>();
</script>

<style module lang="scss">
.select {
  width: 100%;
  padding: 12px 40px 12px 16px;
  font-size: 0.95rem;
  line-height: 1.4;
  border: 2px solid var(--color-border);
  border-radius: 12px;
  background-color: var(--color-background);
  color: var(--color-text);
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  transition: all 0.2s ease;

  background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill='%239ca3af' d='M7.247 11.14 2.451 6.345a1.068 1.068 0 0 1 0-1.51 1.086 1.086 0 0 1 1.519 0l4.006 4.006 4.006-4.006a1.086 1.086 0 0 1 1.519 0 1.068 1.068 0 0 1 0 1.51L8.753 11.14a1.086 1.086 0 0 1-1.506 0z'/%3e%3c/svg%3e");
  background-repeat: no-repeat;
  background-position: right 12px center;
  background-size: 16px 12px;

  &:focus {
    outline: none;
    border-color: var(--color-primary);
    box-shadow: 0 0 0 3px rgba(110, 142, 251, 0.2);
  }

  &:disabled {
    opacity: 0.6;
    cursor: not-allowed;
    background-color: var(--color-secondary);
    background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill='%23d1d5db' d='M7.247 11.14 2.451 6.345a1.068 1.068 0 0 1 0-1.51 1.086 1.086 0 0 1 1.519 0l4.006 4.006 4.006-4.006a1.086 1.086 0 0 1 1.519 0 1.068 1.068 0 0 1 0 1.51L8.753 11.14a1.086 1.086 0 0 1-1.506 0z'/%3e%3c/svg%3e");
  }

  &::-ms-expand {
    display: none;
  }
}
</style>
