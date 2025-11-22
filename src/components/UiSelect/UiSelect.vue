<template>
  <select
    :class="$style.select"
    :value="modelValue"
    @change="$emit('update:modelValue', ($event.target as HTMLSelectElement).value)"
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

defineEmits<{
  (e: 'update:modelValue', value: string): void;
}>();
</script>

<style module lang="scss">
.select {
  width: 100%;
  padding: 12px 16px;
  font-size: 0.95rem;
  line-height: 1.4;
  border: 2px solid var(--color-border);
  border-radius: var(--radius-md);
  background-color: var(--color-background);
  color: var(--color-text);
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  transition: all 0.2s ease;

  &:focus {
    outline: none;
    border-color: var(--color-primary);
    box-shadow: 0 0 0 3px rgba(110, 142, 251, 0.2);
  }

  &:disabled {
    opacity: 0.6;
    cursor: not-allowed;
    background-color: var(--color-secondary);
  }

  // Стилизация стрелки (опционально, можно использовать кастомную)
  &::-ms-expand {
    display: none;
  }

  // Для Firefox
  &:-moz-focusring {
    color: transparent;
    text-shadow: 0 0 0 #000;
  }
}
</style>