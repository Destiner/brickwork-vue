<template>
  <RadioGroup
    :model-value="modelValue"
    class="group"
    @update:model-value="handleUpdate"
  >
    <RadioGroupLabel class="group-label">Plan</RadioGroupLabel>
    <RadioGroupOption
      v-for="option in options"
      :key="option.value"
      v-slot="{ checked }"
      :value="option.value"
      class="option"
    >
      <button
        type="button"
        role="radio"
        :aria-checked="checked"
        :data-state="checked ? 'checked' : 'unchecked'"
      >
        <span
          v-if="checked"
          :data-state="'checked'"
        />
      </button>
      <span class="label">{{ option.label }}</span>
    </RadioGroupOption>
  </RadioGroup>
</template>

<script setup lang="ts">
import { RadioGroup, RadioGroupLabel, RadioGroupOption } from '@headlessui/vue';

defineProps<{
  modelValue: string;
  options: Option[];
}>();

const emit = defineEmits<{
  (e: 'update:modelValue', value: Option): void;
}>();

function handleUpdate(newValue: Option): void {
  emit('update:modelValue', newValue);
}
</script>

<script lang="ts">
interface Option {
  value: string;
  label: string;
}
</script>

<style scoped>
.group-label {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  padding: 0;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border-width: 0;
  white-space: nowrap;
}

.option {
  display: flex;
  align-items: center;
  margin-bottom: var(--gap, 8px);
  outline: none;
  gap: var(--gap-item, 15px);
}

button {
  all: unset;
  width: var(--size-radio, 25px);
  height: var(--size-radio, 25px);
  border: var(--border-radio, none);
  border-radius: var(--border-radius-radio, 100%);
  background: var(--background-radio, white);
  box-shadow: var(--box-shadow-radio, #00000024 0 2px 10px);
}

button > span {
  display: flex;
  position: relative;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
}

button > span::after {
  content: '';
  display: block;
  width: var(--size-radio-indicator, 11px);
  height: var(--size-radio-indicator, 11px);
  border-radius: var(--border-radius-radio-indicator, 100%);
  background: var(--color-radio-indicator, #540502);
}

.label {
  all: unset;
  color: var(--color-label, #540502);
  font-size: var(--font-size-label, 15px);
  font-weight: var(--font-weight-label, 400);
  line-height: var(--line-height-label, 1);
  cursor: default;
}
</style>
