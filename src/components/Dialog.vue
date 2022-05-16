<template>
  <Dialog
    :open="isOpen"
    class="dialog"
    @close="close()"
  >
    <div
      class="backdrop"
      aria-hidden="true"
    />
    <div class="body">
      <DialogPanel class="panel">
        <slot />
      </DialogPanel>
    </div>
  </Dialog>
</template>

<script
  setup
  lang="ts"
>
import { Dialog, DialogPanel } from '@headlessui/vue';

defineProps({
  isOpen: {
    type: Boolean,
    required: true,
  },
});

const emit = defineEmits(['close']);

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
  background: #00000070;
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
  padding: 16px;
}

.panel {
  width: 100%;
  max-width: 384px;
  padding: 8px 16px;
  border-radius: 4px;
  background: var(--color-bg, white);
}
</style>
