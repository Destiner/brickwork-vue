<template>
  <Menu
    as="div"
    class="menu"
  >
    <div>
      <MenuButton class="trigger-button">
        <slot name="trigger" />
      </MenuButton>
    </div>

    <transition name="show">
      <MenuItems class="items">
        <MenuItem
          v-for="option in options"
          :key="option.value"
          v-slot="{ active }"
        >
          <button
            class="item"
            :class="{ active }"
            @click="handleClick(option.value)"
          >
            {{ option.label }}
          </button>
        </MenuItem>
      </MenuItems>
    </transition>
  </Menu>
</template>

<script setup lang="ts">
import { Menu, MenuButton, MenuItems, MenuItem } from '@headlessui/vue';

defineProps<{ options: Option[] }>();

const emit = defineEmits<{ (e: 'select', value: string): void }>();

function handleClick(value: string): void {
  emit('select', value);
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
.menu {
  display: inline-block;
  position: relative;
  text-align: left;
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

.items {
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

.items:focus {
  outline: none;
}

.item {
  display: flex;
  position: relative;
  align-items: center;
  padding: var(--padding-item, 0 12px);
  border: none;
  gap: var(--gap-item, 6px);
  border-radius: var(--border-radius-item, 4px);
  background: none;
  color: var(--color-item, #540502);
  font-size: var(--font-size-item, 12px);
  font-weight: var(--font-weight-item, 400);
  line-height: var(--line-height-item, 1);
  text-align: left;
  white-space: nowrap;
  cursor: default;
  user-select: none;
}

.item.active {
  background: var(--background-item-active, #540502);
  color: var(--color-item-active, white);
}
</style>
