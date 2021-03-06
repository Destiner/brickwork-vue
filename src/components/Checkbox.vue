<template>
  <div>
    <button
      :id="id"
      type="button"
      role="checkbox"
      :aria-checked="modelValue"
      :data-state="dataState"
      @click="handleClick"
    >
      <span
        v-if="modelValue"
        data-state="checked"
      >
        <svg
          width="15"
          height="15"
          viewBox="0 0 15 15"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M11.4669 3.72684C11.7558 3.91574 11.8369 4.30308 11.648 4.59198L7.39799 11.092C7.29783 11.2452 7.13556 11.3467 6.95402 11.3699C6.77247 11.3931 6.58989 11.3355 6.45446 11.2124L3.70446 8.71241C3.44905 8.48022 3.43023 8.08494 3.66242 7.82953C3.89461 7.57412 4.28989 7.55529 4.5453 7.78749L6.75292 9.79441L10.6018 3.90792C10.7907 3.61902 11.178 3.53795 11.4669 3.72684Z"
            fill="currentColor"
            fill-rule="evenodd"
            clip-rule="evenodd"
          />
        </svg>
      </span>
    </button>
    <label
      v-if="label"
      :for="id"
    >
      {{ label }}
    </label>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const props = withDefaults(
  defineProps<{
    modelValue: boolean;
    label: string;
  }>(),
  {
    label: '',
  },
);

const emit = defineEmits<{ (e: 'update:modelValue', value: boolean): void }>();

const id = computed(() => `checkbox-${Math.random().toString().substring(2)}`);
const dataState = computed(() => (props.modelValue ? 'checked' : 'unchecked'));

function handleClick(): void {
  emit('update:modelValue', !props.modelValue);
}
</script>

<style scoped>
div {
  display: flex;
  align-items: center;
  gap: var(--gap, 15px);
}

button {
  all: unset;
  display: flex;
  align-items: center;
  justify-content: center;
  width: var(--size-check, 25px);
  height: var(--size-check, 25px);
  border: var(--border-check, none);
  border-radius: var(--border-radius-check, 4px);
  background: var(--background-check, white);
  box-shadow: var(--box-shadow-check, #00000024 0 2px 10px);
}

button > span {
  display: flex;
  color: var(--color-check, #540502);
  pointer-events: none;
}

label {
  all: unset;
  color: var(--color-label, #540502);
  font-size: var(--font-size-label, 15px);
  font-weight: var(--font-weight-label, 400);
  text-align: left;
  cursor: default;
}
</style>
