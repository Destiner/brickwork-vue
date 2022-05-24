<template>
  <Listbox
    :model-value="selectedItem"
    @update:model-value="handleUpdate"
  >
    <div class="select">
      <ListboxButton class="trigger">
        <slot
          name="trigger"
          :selected-item="selectedItem"
        />
      </ListboxButton>

      <transition name="show">
        <ListboxOptions class="options">
          <ListboxOption
            v-for="item in items"
            v-slot="{ active, selected }"
            :key="item.value"
            :value="item"
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
                  width="14"
                  height="14"
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
              <span class="option-label">
                {{ item.label }}
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
  items: {
    type: Array as PropType<Option[]>,
    required: true,
  },
});

const emit = defineEmits(['update:modelValue']);

const selectedItem = computed(() =>
  props.items.find((item) => item.value === props.modelValue),
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
  --trigger-height: 35px;

  display: flex;
  position: relative;
  margin-top: 4px;
}

.trigger {
  all: unset;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  height: var(--trigger-height);
  padding: var(--padding-trigger, 0 15px);
  border-radius: var(--border-radius-trigger, 4px);
  background-color: var(--color-trigger-bg, white);
  box-shadow: var(--box-shadow-trigger, #00000024 0 2px 10px);
  color: var(--color-trigger-label, #540502);
  font-size: var(--font-size-trigger, 13px);
  font-weight: var(--font-weight-trigger, 400);
  line-height: 1;
  gap: 5px;
}

.trigger:hover {
  background-color: var(--color-trigger-bg-hover, #eee);
}

.trigger:focus {
  box-shadow: var(--color-outline, #290402) 0 0 0 2px;
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
  margin-top: calc(var(--trigger-height) + 4px);
  padding: var(--padding-list, 4px);
  overflow: auto;
  border-radius: var(--radius-list, 6px);
  background: var(--color-list-bg, white);
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
  padding: var(--padding-item, 0 12px);
  gap: var(--gap-item, 6px);
  border-radius: var(--border-radius-item, 4px);
  color: var(--color-item-label, #540502);
  font-size: var(--font-size-item, 12px);
  font-weight: var(--font-weight-item, 400);
  line-height: 25px;
  text-align: left;
  cursor: default;
  user-select: none;
}

.option.active {
  background: var(--color-item-bg-active, #540502);
  color: var(--color-item-label-active, white);
}

.option-label {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.option-selected-icon {
  display: flex;
  align-items: center;
}
</style>
