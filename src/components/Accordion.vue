<template>
  <div class="container">
    <Disclosure
      v-for="(item, index) in items"
      :key="index"
      as="div"
      class="item"
    >
      <div class="divider" />
      <DisclosureButton class="button">
        {{ item.header }}
      </DisclosureButton>
      <DisclosurePanel class="panel">
        {{ item.text }}
      </DisclosurePanel>
    </Disclosure>
  </div>
</template>

<script setup lang="ts">
import { Disclosure, DisclosureButton, DisclosurePanel } from '@headlessui/vue';

defineProps<{
  items: Item[];
}>();
</script>

<script lang="ts">
interface Item {
  header: string;
  text: string;
}

// eslint-disable-next-line import/prefer-default-export
export { Item };
</script>

<style scoped>
.container {
  display: flex;
  gap: var(--gap, 0);
  flex-direction: column;
  width: 100%;
  padding: var(--padding, 0);
  border-radius: var(--border-radius, 6px);
  background: var(--background, white);
}

.divider {
  width: 100%;
  height: var(--height-divider, 1px);
  background: var(--background-divider, #e5e2e4);
}

.item:first-child > .divider {
  display: none;
}

.button {
  display: flex;
  justify-content: space-between;
  width: 100%;
  margin: 0;
  padding: var(--padding-button, 12px 20px);
  border: none;
  border-radius: var(--border-radius-button, 6px);
  background: var(--background-button, white);
  color: var(--color-button, #540502);
  font-size: var(--font-size-button, 15px);
  font-weight: 400;
  text-align: left;
  cursor: pointer;
}

.button:hover {
  background: var(--background-button-hover, #f9f8f9);
}

.panel {
  padding: var(--padding-panel, 15px 20px);
  border-top: var(--height-divider, 1px) solid
    var(--background-divider, #e5e2e4);
  background: var(--background-panel, #f9f8f9);
  color: var(--color-panel, #6f6e77);
  font-size: var(--font-size-panel, 15px);
  text-align: left;
}
</style>
