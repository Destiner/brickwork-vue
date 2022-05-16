<template>
  <div>
    <button
      id="checkbox"
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
      for="checkbox"
    >
      {{ label }}
    </label>
  </div>
</template>

<script
  setup
  lang="ts"
>
import { computed } from 'vue';

const props = defineProps({
  modelValue: {
    type: Boolean,
    required: true,
  },
  label: {
    type: String,
    default: '',
  },
});

const emit = defineEmits(['update:modelValue']);

const dataState = computed(() => (props.modelValue ? 'checked' : 'unchecked'));

function handleClick(): void {
  emit('update:modelValue', !props.modelValue);
}
</script>

<style scoped>
div {
  display: flex;
  align-items: center;
  gap: 15px;
}

button {
  all: unset;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 25px;
  height: 25px;
  border-radius: 4px;
  background-color: white;
  box-shadow: #00000024 0 2px 10px;
}

button > span {
  display: flex;
  color: #540502;
  pointer-events: none;
}

label {
  all: unset;
  color: #540502;
  font-size: 15px;
  text-align: left;
  cursor: default;
}
</style>
