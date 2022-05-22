<template>
  <fieldset>
    <label
      v-if="label"
      :for="id"
    >
      {{ label }}
    </label>
    <input
      :id="id"
      :value="modelValue"
      :placeholder="placeholder"
      @input="handleInput"
    />
  </fieldset>
</template>

<script
  setup
  lang="ts"
>
import { computed } from 'vue';

defineProps({
  modelValue: {
    type: String,
    required: true,
  },
  label: {
    type: String,
    default: '',
  },
  placeholder: {
    type: String,
    default: '',
  },
});

const emit = defineEmits(['update:modelValue']);

const id = computed(() => `input-${Math.random().toString().substring(2)}`)

function handleInput(e: Event): void {
  const value = (e.target as HTMLInputElement).value;
  emit('update:modelValue', value);
}
</script>

<style scoped>
fieldset {
  all: unset;
  display: flex;
  flex-direction: var(--direction, column);
  align-items: var(--align, start);
  gap: var(--gap, 4px);
}

label {
  all: unset;
  flex: var(--flex-label, initial);
  color: var(--color-label, #540502);
  font-size: var(--font-size-label, 15px);
  font-weight: var(--font-weight-label, 400);
  text-align: right;
  cursor: default;
}

input {
  all: unset;
  display: inline-flex;
  box-sizing: border-box;
  flex: var(--flex-input, initial);
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 35px;
  padding: 0 10px;
  border-radius: 4px;
  box-shadow: var(--color-outline, #c99894) 0 0 0 1px;
  color: var(--color-text, #540502);
  font-size: var(--font-size, 15px);
  font-weight: var(--font-weight, 400);
  line-height: 1;
}

input:focus {
  box-shadow: var(--color-outline, #c99894) 0 0 0 2px;
}
</style>
