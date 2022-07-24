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
      ref="input"
      :value="modelValue"
      :placeholder="placeholder"
      @input="handleInput"
    />
  </fieldset>
</template>

<script setup lang="ts">
import { computed, onMounted, ref } from 'vue';

withDefaults(
  defineProps<{
    modelValue: string;
    label: string;
    placeholder: string;
  }>(),
  {
    label: '',
    placeholder: '',
  },
);

const emit = defineEmits<{
  (e: 'init', value: HTMLInputElement): void;
  (e: 'update:modelValue', value: string): void;
}>();

onMounted(() => {
  emit('init', input.value);
});

const input = ref<HTMLInputElement | null>(null);

const id = computed(() => `input-${Math.random().toString().substring(2)}`);

function handleInput(e: Event): void {
  const value = (e.target as HTMLInputElement).value;
  emit('update:modelValue', value);
}
</script>

<style scoped>
fieldset {
  all: unset;
  display: flex;
  flex-direction: var(--flex-direction, column);
  align-items: var(--align-items, start);
  gap: var(--gap, 4px);
}

label {
  all: unset;
  flex: var(--flex-label, initial);
  color: var(--color-label, #540502);
  font-size: var(--font-size-label, 12px);
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
  padding: var(--padding-input, 7px 10px);
  border: var(--border-input, 1px solid #c99894);
  border-radius: var(--border-radius-input, 4px);
  background: var(--background-input, white);
  color: var(--color-input, #540502);
  font-size: var(--font-size-input, 15px);
  font-weight: var(--font-weight-input, 400);
  line-height: var(--line-height-input, 1);
}

input:focus {
  border: var(--border-input-focus, 1px solid #ae8380);
  background: var(--background-input-focus, white);
}
</style>
