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
        class="brix"
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

<script
  setup
  lang="ts"
>
import { RadioGroup, RadioGroupLabel, RadioGroupOption } from '@headlessui/vue';
import { PropType } from 'vue';

defineProps({
  modelValue: {
    type: String,
    required: true,
  },
  options: {
    type: Array as PropType<Option[]>,
    required: true,
  },
});

const emit = defineEmits(['update:modelValue']);

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
  margin-bottom: 8px;
}

button.brix {
  width: 25px;
  height: 25px;
  border-radius: 100%;
  background-color: white;
  box-shadow: #00000024 0 2px 10px;
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
  width: 11px;
  height: 11px;
  border-radius: 50%;
  background-color: #540502;
}

.label {
  padding-left: 15px;
  font-size: 15px;
  line-height: 1;
}

button {
  all: unset;
}
</style>
