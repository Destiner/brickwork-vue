<template>
  <Listbox
    :model-value="selectedOption"
    @update:model-value="handleUpdate"
  >
    <div class="select">
      <ListboxButton class="trigger">
        <slot
          name="trigger"
          :selected-item="selectedOption"
        />
      </ListboxButton>

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

<script
  setup
  lang="ts"
>
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
});

const emit = defineEmits(['update:modelValue']);

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
  --height-trigger: 35px;

  display: flex;
  position: relative;
  margin-top: 4px;
}

.trigger {
  all: unset;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  height: var(--height-trigger);
  padding: var(--padding-trigger, 0 15px);
  border: var(--border-trigger, 1px solid transparent);
  border-radius: var(--border-radius-trigger, 4px);
  background: var(--background-trigger, white);
  box-shadow: var(--box-shadow-trigger, #00000024 0 2px 10px);
  color: var(--color-trigger, #540502);
  font-size: var(--font-size-trigger, 13px);
  font-weight: var(--font-weight-trigger, 400);
  line-height: 1;
  gap: 5px;
}

.trigger:hover {
  background: var(--background-trigger-hover, #eee);
}

.trigger:focus {
  border: var(--border-trigger-focus, 1px solid #290402);
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
  flex-direction: column;
  max-height: 240px;
  margin-top: calc(var(--height-trigger) + 4px);
  padding: var(--padding-list, 4px);
  overflow: auto;
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
  line-height: 25px;
  text-align: left;
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
