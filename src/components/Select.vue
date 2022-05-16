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
              <span class="option-label">
                {{ item.label }}
              </span>
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
  padding: 0 15px;
  border-radius: 4px;
  background-color: white;
  box-shadow: #00000024 0 2px 10px;
  color: #540502;
  font-size: 13px;
  line-height: 1;
  gap: 5px;
}

.trigger:hover {
  background-color: #eee;
}

.trigger:focus {
  box-shadow: #290402 0 0 0 2px;
}

.content {
  overflow: hidden;
  border-radius: 6px;
  background-color: white;
  box-shadow: 0 10px 38px -10px #1617185a, 0 10px 20px -15px #16171833;
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
  padding: 4px;
  overflow: auto;
  border-radius: 4px;
  background: white;
  box-shadow: 0 10px 15px -3px rgb(0 0 0 / 10%), 0 4px 6px -4px rgb(0 0 0 / 10%);
  font-size: 1rem;
}

.options:focus {
  outline: none;
}

.option {
  display: inline-block;
  position: relative;
  padding: 0 25px;
  border-radius: 4px;
  color: #540502;
  font-size: 12px;
  line-height: 25px;
  text-align: left;
  cursor: default;
  user-select: none;
}

.option.active {
  background: #540502;
  color: white;
}

.option-label {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.option-selected-icon {
  display: flex;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  align-items: center;
  padding-left: 6px;
}
</style>
