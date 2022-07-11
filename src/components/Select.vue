<template>
  <Listbox
    :model-value="selectedOption"
    @update:model-value="handleUpdate"
  >
    <div class="select">
      <div class="trigger">
        <label
          v-if="label"
          :for="id"
        >
          {{ label }}
        </label>
        <ListboxButton
          :id="id"
          class="trigger-button"
        >
          <slot
            name="trigger"
            :selected-item="selectedOption"
          />
        </ListboxButton>
      </div>

      <transition name="show">
        <ListboxOptions class="options">
          <ListboxOption
            v-for="option in options"
            v-slot="{ active, selected }"
            :key="option.value"
            :value="option"
            as="template"
          >
            <li
              class="option"
              :class="{ active }"
            >
              <span
                v-if="selected"
                class="option-selected-icon"
              >
                <svg
                  width="100%"
                  height="100%"
                  viewBox="0 0 15 15"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path
                    fill="currentColor"
                    fill-rule="evenodd"
                    d="M11.467 3.727c.289.189.37.576.181.865l-4.25 6.5a.625.625 0 0 1-.944.12l-2.75-2.5a.625.625 0 0 1 .841-.925l2.208 2.007l3.849-5.886a.625.625 0 0 1 .865-.181Z"
                    clip-rule="evenodd"
                  />
                </svg>
              </span>
              <span
                class="option-label"
                :class="{ selected }"
              >
                {{ option.label }}
              </span>
            </li>
          </ListboxOption>
        </ListboxOptions>
      </transition>
    </div>
  </Listbox>
</template>

<script setup lang="ts">
import {
  Listbox,
  ListboxButton,
  ListboxOptions,
  ListboxOption,
} from '@headlessui/vue';
import { PropType, computed } from 'vue';

const props = defineProps({
  modelValue: {
    type: String,
    required: true,
  },
  options: {
    type: Array as PropType<Option[]>,
    required: true,
  },
  label: {
    type: String,
    default: '',
  },
});

const emit = defineEmits(['update:modelValue']);

const id = computed(() => `select-${Math.random().toString().substring(2)}`);

const selectedOption = computed(() =>
  props.options.find((option) => option.value === props.modelValue),
);

function handleUpdate(option: Option): void {
  emit('update:modelValue', option.value);
}
</script>

<script lang="ts">
interface Option {
  value: string;
  label: string;
}

// eslint-disable-next-line import/prefer-default-export
export { Option };
</script>

<style scoped>
.select {
  all: unset;
  position: relative;
}

.trigger {
  all: unset;
  display: flex;
  position: relative;
  flex-direction: var(--flex-direction-trigger, column);
  align-items: var(--align-items-trigger, start);
  gap: var(--gap-trigger, 4px);
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

.trigger-button {
  all: unset;
  display: inline-flex;
  flex: var(--flex-button, initial);
  align-items: center;
  justify-content: center;
  padding: var(--padding-button, 10px 15px);
  border: var(--border-button, 1px solid transparent);
  border-radius: var(--border-radius-button, 4px);
  background: var(--background-button, white);
  box-shadow: var(--box-shadow-button, #00000024 0 2px 10px);
  color: var(--color-button, #540502);
  font-size: var(--font-size-button, 13px);
  font-weight: var(--font-weight-button, 400);
  line-height: var(--line-height-button, 1);
  gap: 5px;
}

.trigger-button:hover {
  background: var(--background-button-hover, #eee);
  box-shadow: var(--box-shadow-button-hover, #00000024 0 2px 10px);
}

.trigger-button:focus {
  border: var(--border-button-focus, 1px solid #290402);
}

.show-enter-active,
.show-leave-active {
  transition: opacity 0.1s ease-in;
}

.show-enter-from,
.show-leave-to {
  opacity: 0;
}

.options {
  display: flex;
  position: absolute;
  z-index: 1;
  flex-direction: column;
  max-height: 240px;
  margin-top: var(--gap, 4px);
  padding: var(--padding-list, 4px);
  overflow: auto;
  border: var(--border-list, none);
  border-radius: var(--border-radius-list, 6px);
  background: var(--background-list, white);
  box-shadow: var(
    --box-shadow-list,
    0 10px 15px -3px rgb(0 0 0 / 10%),
    0 4px 6px -4px rgb(0 0 0 / 10%)
  );
}

.options:focus {
  outline: none;
}

.option {
  display: flex;
  position: relative;
  align-items: center;
  padding: var(--padding-item, 0 12px);
  gap: var(--gap-item, 6px);
  border-radius: var(--border-radius-item, 4px);
  color: var(--color-item, #540502);
  font-size: var(--font-size-item, 12px);
  font-weight: var(--font-weight-item, 400);
  line-height: var(--line-height-item, 1);
  text-align: left;
  white-space: nowrap;
  cursor: default;
  user-select: none;
}

.option.active {
  background: var(--background-item-active, #540502);
  color: var(--color-item-active, white);
}

.option-label {
  padding-left: calc(var(--gap-item, 6px) + var(--size-item-active-icon, 14px));
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.option-label.selected {
  padding-left: 0;
}

.option-selected-icon {
  display: flex;
  width: var(--size-item-active-icon, 14px);
  height: var(--size-item-active-icon, 14px);
}
</style>
