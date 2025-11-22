<template>
  <button
    :class="$style.button"
    :data-layout="props.layout"
    :disabled="props.isDisabled"
    :type="props.type"
  >
    <slot></slot>
  </button>
</template>

<script setup lang="ts">
interface IProps {
  layout?: 'primary' | 'secondary' | 'outline';
  type?: 'submit' | 'button';
  isDisabled?: boolean;
}

const props = withDefaults(defineProps<IProps>(), {
  layout: 'primary',
  type: 'button',
  isDisabled: false,
});
</script>

<style module lang="scss">
.button {
  position: relative;
  display: inline-flex;
  gap: 8px;
  align-items: center;
  justify-content: center;
  height: 44px;
  padding: 12px 24px;
  font-size: 0.95rem;
  font-weight: 500;
  line-height: 1.4;
  border: none;
  border-radius: 12px;
  cursor: pointer;
  transition: all 0.2s ease;

  &:disabled {
    opacity: 0.6;
    cursor: not-allowed;
    transform: none;
    box-shadow: none;
  }

  &[data-layout='primary'] {
    color: #ffffff;
    background: linear-gradient(135deg, #6e8efb, #a777e3);
    box-shadow: 0 4px 12px rgba(110, 142, 251, 0.3);

    &:hover:not(:disabled) {
      transform: translateY(-2px);
      box-shadow: 0 6px 16px rgba(110, 142, 251, 0.4);
    }

    &:active:not(:disabled) {
      transform: translateY(0);
    }
  }

  &[data-layout='secondary'] {
    color: #4b5563;
    background-color: #f3f4f6;
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.05);

    &:hover:not(:disabled) {
      background-color: #e5e7eb;
      transform: translateY(-1px);
    }

    &:active:not(:disabled) {
      transform: translateY(0);
    }
  }

  &[data-layout='outline'] {
    color: #6e8efb;
    background: transparent;
    border: 2px solid #6e8efb;
    box-shadow: none;

    &:hover:not(:disabled) {
      background: rgba(110, 142, 251, 0.08);
      transform: translateY(-1px);
    }

    &:active:not(:disabled) {
      transform: translateY(0);
    }
  }
}
</style>
