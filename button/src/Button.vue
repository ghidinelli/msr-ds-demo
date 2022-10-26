<template>
  <button :class="variant">
    <slot></slot>
  </button>
</template>

<script setup lang="ts">
import { PropType } from 'vue';

const props = defineProps({
  /**
   * The variant of the button - either 'primary' or 'secondary'
   * @example 'secondary'
   */
  variant: {
    type: String as PropType<'primary' | 'secondary'>,
    default: 'primary',
    validator: (value: any) => ['primary', 'secondary'].includes(value),
  },
});
</script>

<style lang="scss" scoped>
@import '../../tokens/variables.scss';

button {

  &.primary {
    color: var(--vue-color-text-on-primary);
    background-color: $figma-global-button-primary-background;
  }

  &.secondary {
    background-color: var(--vue-color-secondary);
    color: var(--vue-color-text-on-secondary);
  }

  &.disabled,
  &:disabled {
    background-color: transparent;
    pointer-events: none;
    filter: brightness(50%);
  }

  &:hover {
    color: var(--vue-color-text-on-primary);
    filter: brightness(1.1);
  }
}
</style>
