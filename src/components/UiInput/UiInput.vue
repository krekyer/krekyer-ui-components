<template>
  <div :class="$style.wrapper">
    <input
      :class="$style.input"
      :value="modelValue"
      @input="
        $emit('update:modelValue', ($event.target as HTMLInputElement).value)
      "
      :disabled="isDisabled"
      :placeholder="placeholder"
      :data-disabled="isDisabled"
    />
  </div>
</template>

<script setup lang="ts">
defineProps<{
  modelValue: string;
  isDisabled?: boolean;
  placeholder?: string;
}>();

defineEmits<{
  (e: 'update:modelValue', value: string): void;
}>();
</script>

<style module lang="scss">
.wrapper {
  position: relative;
  width: 100%;
}

.input {
  width: 100%;
  padding: 12px 16px;
  font-size: 0.95rem;
  line-height: 1.4;
  border: 2px solid #d1d5db;
  border-radius: 12px;
  background-color: #ffffff;
  color: #4b5563;
  transition: all 0.2s ease;

  &:focus {
    outline: none;
    border-color: var(--color-primary);
    box-shadow: 0 0 0 3px rgba(110, 142, 251, 0.2);
  }
  &:disabled {
    opacity: 0.6;
    cursor: not-allowed;
    background-color: #f3f4f6;
  }

  &::placeholder {
    color: #9ca3af;
    opacity: 1;
  }
}
</style>
