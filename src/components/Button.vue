<template>
  <button>{{ label }}</button>
</template>

<script
  lang="ts"
  setup
>
defineProps({
  label: {
    type: String,
    required: true,
  },
});
</script>

<style scoped>
button {
  all: unset;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: var(--padding, 10px 16px);
  border-radius: var(--border-radius, 4px);
  background: var(--color-bg, #fafafa);
  box-shadow: #00000024 0 2px 10px;
  color: var(--color-label, #540502);
  font-size: var(--font-size-label, 15px);
  font-weight: var(--font-weight-label, 500);
  line-height: 1;
  text-decoration: none;
}

button:focus {
  box-shadow: var(--color-outline, #290402) 0 0 0 2px;
}

button:hover {
  background-color: var(--color-bg-hover, #eee);
}
</style>
