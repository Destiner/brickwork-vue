<template>
  <div class="container">
    <Switch
      :model-value="modelValue"
      class="switch"
      :class="{ enabled: modelValue }"
      @update:model-value="handleUpdate"
    >
      <span class="label">{{ label }}</span>
      <span
        aria-hidden="true"
        :class="{ enabled: modelValue }"
        class="thumb"
      />
    </Switch>
  </div>
</template>

<script setup lang="ts">
import { Switch } from '@headlessui/vue';

withDefaults(
  defineProps<{
    modelValue: boolean;
    label: string;
  }>(),
  {
    label: '',
  },
);

const emit = defineEmits<{
  (e: 'update:modelValue', value: boolean): void;
}>();

function handleUpdate(value: boolean): void {
  emit('update:modelValue', value);
}
</script>

<style scoped>
.container {
  padding: 64px 0;
}

.container > :deep(.switch) {
  display: inline-flex;
  position: relative;
  flex-shrink: 0;
  align-items: center;
  width: var(--width, 42px);
  height: var(--height, 25px);
  padding: 0;
  transition: background cubic-bezier(0, 0, 0.2, 1) 200ms;
  border-radius: calc(var(--height, 25px) / 2);
  border-color: transparent;
  background: var(--background, #00000070);
  box-shadow: var(--box-shadow, #00000024 0 2px 10px);
  cursor: pointer;
}

.container > :deep(.switch.enabled) {
  background: var(--background-hover, black);
}

.label {
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

.thumb {
  display: inline-block;
  width: var(--size-thumb, 21px);
  height: var(--size-thumb, 21px);
  transform: translateX(0);
  transition: transform cubic-bezier(0, 0, 0.2, 1) 200ms;
  border-radius: 50%;
  background: var(--color-thumb, white);
  box-shadow: var(--box-shadow-thumb, #00000024 0 2px 2px);
  pointer-events: none;
}

.thumb.enabled {
  transform: translateX(
    calc(var(--width, 42px) - var(--size-thumb, 21px) - 4px)
  );
}
</style>
