<template>
  <button>
    <slot />
  </button>
</template>

<style scoped>
button {
  all: unset;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: var(--padding, 10px 16px);
  border: var(--border, none);
  border-radius: var(--border-radius, 4px);
  background: var(--background, #fafafa);
  box-shadow: var(--box-shadow, #00000024 0 2px 10px);
  color: var(--color, #540502);
  font-size: var(--font-size, 15px);
  font-weight: var(--font-weight, 500);
  line-height: var(--line-height, 1);
}

button:hover {
  border: var(--border-hover, none);
  background: var(--background-hover, #eee);
  box-shadow: var(--box-shadow-hover, #00000024 0 2px 10px);
}

button:disabled {
  background: var(--background-disabled, #ccc);
  color: var(--color-disabled, #3b0301);
}
</style>
