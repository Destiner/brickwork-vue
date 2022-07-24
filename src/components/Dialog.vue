<template>
  <TransitionRoot
    appear
    :show="isOpen"
    as="template"
  >
    <Dialog
      class="dialog"
      @close="close()"
    >
      <TransitionChild
        as="template"
        enter="backdrop-enter"
        enter-from="backdrop-enter-from"
        enter-to="backdrop-enter-to"
        leave="backdrop-leave"
        leave-from="backdrop-leave-from"
        leave-to="backdrop-leave-to"
      >
        <div
          class="backdrop"
          aria-hidden="true"
        />
      </TransitionChild>
      <div class="body">
        <TransitionChild
          as="template"
          enter="panel-enter"
          enter-from="panel-enter-from"
          enter-to="panel-enter-to"
          leave="panel-leave"
          leave-from="panel-leave-form"
          leave-to="panel-leave-to"
        >
          <DialogPanel class="panel">
            <slot />
          </DialogPanel>
        </TransitionChild>
      </div>
    </Dialog>
  </TransitionRoot>
</template>

<script setup lang="ts">
import {
  Dialog,
  DialogPanel,
  TransitionChild,
  TransitionRoot,
} from '@headlessui/vue';

defineProps<{ isOpen: boolean }>();

const emit = defineEmits<{ (e: 'close'): void }>();

function close(): void {
  emit('close');
}
</script>

<style scoped>
.dialog {
  position: relative;
  z-index: 1;
}

.backdrop {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background: var(--background-backdrop, #00000070);
}

.body {
  display: flex;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  align-items: center;
  justify-content: center;
}

.panel {
  width: var(--width, 450px);
  max-height: var(--max-height, 85vh);
  padding: var(--padding, 25px);
  border-radius: var(--border-radius, 6px);
  background: var(--background, white);
}

.backdrop-enter {
  transition: var(--transition-backdrop-enter, all 300ms ease-out);
}

.backdrop-enter-from {
  opacity: var(--opacity-backdrop-enter-from, 0);
}

.backdrop-enter-to {
  opacity: var(--opacity-backdrop-enter-to, 1);
}

.backdrop-leave {
  transition: var(--transition-backdrop-leave, all 200ms ease-in);
}

.backdrop-leave-from {
  opacity: var(--opacity-backdrop-leave-from, 1);
}

.backdrop-leave-to {
  opacity: var(--opacity-backdrop-leave-to, 0);
}

.panel-enter {
  transition: var(--transition-panel-enter, all 300ms ease-out);
}

.panel-enter-from {
  transform: var(--transform-panel-enter-from, scale(0.95));
  opacity: var(--opacity-panel-enter-from, 0);
}

.panel-enter-to {
  transform: var(--transform-panel-enter-to, scale(1));
  opacity: var(--opacity-panel-enter-to, 1);
}

.panel-leave {
  transition: var(--transition-panel-leave, all 200ms ease-in);
}

.panel-leave-form {
  transform: var(--transform-panel-leave-from, scale(1));
  opacity: var(--opacity-panel-leave-from, 1);
}

.panel-leave-to {
  transform: var(--transform-panel-leave-to, scale(0.95));
  opacity: var(--opacity-panel-leave-to, 0);
}
</style>
