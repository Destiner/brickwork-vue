<template>
  <button
    class="brix"
    type="button"
    role="checkbox"
    :aria-checked="modelValue"
    :data-state="dataState"
    @click="handleClick"
  >
    <span
      v-if="modelValue"
      data-state="checked"
    >
      <svg
        width="15"
        height="15"
        viewBox="0 0 15 15"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M11.4669 3.72684C11.7558 3.91574 11.8369 4.30308 11.648 4.59198L7.39799 11.092C7.29783 11.2452 7.13556 11.3467 6.95402 11.3699C6.77247 11.3931 6.58989 11.3355 6.45446 11.2124L3.70446 8.71241C3.44905 8.48022 3.43023 8.08494 3.66242 7.82953C3.89461 7.57412 4.28989 7.55529 4.5453 7.78749L6.75292 9.79441L10.6018 3.90792C10.7907 3.61902 11.178 3.53795 11.4669 3.72684Z"
          fill="currentColor"
          fill-rule="evenodd"
          clip-rule="evenodd"
        />
      </svg>
    </span>
  </button>
</template>

<script
  setup
  lang="ts"
>
import { computed } from 'vue';

const props = defineProps({
  modelValue: {
    type: Boolean,
    required: true,
  },
});

const emit = defineEmits(['update:modelValue']);

const dataState = computed(() => (props.modelValue ? 'checked' : 'unchecked'));

function handleClick(): void {
  emit('update:modelValue', !props.modelValue);
}
</script>

<style scoped>
button.brix {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 25px;
  height: 25px;
  border-radius: 4px;
  background-color: white;
  box-shadow: #00000024 0 2px 10px;
}

button.brix > span {
  display: flex;
  color: #540502;
  pointer-events: none;
}

button {
  content: unset;
  quotes: unset;
  visibility: unset;
  position: unset;
  z-index: unset;
  top: unset;
  right: unset;
  bottom: unset;
  left: unset;
  box-sizing: unset;
  grid-area: unset;
  grid-auto-columns: unset;
  grid-auto-flow: unset;
  grid-auto-rows: unset;
  grid-column: unset;
  grid-row-end: unset;
  grid-template: unset;
  grid-template-areas: unset;
  grid-template-columns: unset;
  flex: unset;
  flex-flow: unset;
  align-content: unset;
  align-self: unset;
  order: unset;
  width: unset;
  min-width: unset;
  max-width: unset;
  min-height: unset;
  max-height: unset;
  block-size: unset;
  min-block-size: unset;
  max-block-size: unset;
  inline-size: unset;
  min-inline-size: unset;
  max-inline-size: unset;
  margin: unset;
  margin-right: unset;
  margin-bottom: unset;
  margin-left: unset;
  margin-block-start: unset;
  margin-block-end: unset;
  margin-inline-start: unset;
  margin-inline-end: unset;
  padding-block-start: unset;
  padding-block-end: unset;
  padding-inline-start: unset;
  padding-inline-end: unset;
  float: unset;
  clear: unset;
  color-scheme: unset;
  overflow-x: unset;
  overflow-y: unset;
  overflow-wrap: unset;
  clip: unset;
  zoom: unset;
  columns: unset;
  column-gap: unset;
  column-fill: unset;
  column-rule: unset;
  column-span: unset;
  table-layout: unset;
  empty-cells: unset;
  caption-side: unset;
  border-collapse: unset;
  transform: unset;
  transform-box: unset;
  transform-style: unset;
  perspective: unset;
  transition: unset;
  transition-property: unset;
  transition-duration: unset;
  transition-delay: unset;
  animation: unset;
  animation-name: unset;
  animation-duration: unset;
  animation-play-state: unset;
  animation-delay: unset;
  animation-iteration-count: unset;
  animation-direction: unset;
  animation-fill-mode: unset;
  border-top: unset;
  border-right: unset;
  border-bottom: unset;
  border-left: unset;
  outline: unset;
  outline-offset: unset;
  outline-style: unset;
  stroke-width: unset;
  stroke-linecap: unset;
  stroke-dasharray: unset;
  stroke-dashoffset: unset;
  stroke: unset;
  stroke-linejoin: unset;
  stroke-miterlimit: unset;
  stroke-opacity: unset;
  opacity: unset;
  background-attachment: unset;
  background-blend-mode: unset;
  background-clip: unset;
  background-color: unset;
  background-image: unset;
  background-origin: unset;
  background-position-x: unset;
  background-position-y: unset;
  background-size: unset;
  box-shadow: unset;
  fill: unset;
  font-family: unset;
  font-feature-settings: unset;
  -webkit-font-smoothing: unset;
  font-optical-sizing: unset;
  font-stretch: unset;
  font-style: unset;
  font-synthesis: unset;
  font-variant-alternates: unset;
  font-variant-caps: unset;
  font-variant-east-asian: unset;
  font-variant-ligatures: unset;
  font-variant-numeric: unset;
  font-variant-position: unset;
  font-variation-settings: unset;
  letter-spacing: unset;
  list-style: unset;
  text-align: unset;
  text-anchor: unset;
  text-decoration: unset;
  text-decoration-skip: unset;
  text-decoration-thickness: unset;
  text-indent: unset;
  text-overflow: unset;
  text-rendering: unset;
  text-shadow: unset;
  text-transform: unset;
  text-underline-offset: unset;
  text-underline-position: unset;
  word-wrap: unset;
  word-break: unset;
  vertical-align: unset;
  white-space: unset;
  word-spacing: unset;
  src: unset;
  tab-size: unset;
  counter-reset: unset;
  counter-increment: unset;
  writing-mode: unset;
  resize: unset;
  -webkit-locale: unset;
  -webkit-text-zoom: unset;
  additive-symbols: unset;
  alt: unset;
  aspect-ratio: unset;
  border-block-end: unset;
  border-block-end-width: unset;
  border-block-end-color: unset;
  border-block-start: unset;
  border-end-end-radius: unset;
  border-end-start-radius: unset;
  border-image: unset;
  border-inline-end: unset;
  border-inline-start: unset;
  border-start-end-radius: unset;
  border-start-start-radius: unset;
  break-after: unset;
  break-before: unset;
  break-inside: unset;
  caret-color: unset;
  clip-path: unset;
  clip-rule: unset;
  color-interpolation-filters: unset;
  contain: unset;
  cursor: unset;
  enable-background: unset;
  fallback: unset;
  fill-opacity: unset;
  fill-rule: unset;
  filter: unset;
  flood-color: unset;
  flood-opacity: unset;
  font-display: unset;
  glyph-orientation-horizontal: unset;
  glyph-orientation-vertical: unset;
  hanging-punctuation: unset;
  image-orientation: unset;
  image-rendering: unset;
  inset-block-end: unset;
  inset-block-start: unset;
  inset-inline-end: unset;
  inset-inline-start: unset;
  isolation: unset;
  justify-items: unset;
  justify-self: unset;
  kerning: unset;
  lighting-color: unset;
  line-break: unset;
  marker-end: unset;
  marker-mid: unset;
  marker-start: unset;
  mask: unset;
  mask-type: unset;
  math-style: unset;
  mix-blend-mode: unset;
  negative: unset;
  object-fit: unset;
  object-position: unset;
  orphans: unset;
  overscroll-behavior-x: unset;
  overscroll-behavior-y: unset;
  pad: unset;
  paint-order: unset;
  pointer-events: unset;
  prefix: unset;
  range: unset;
  rotate: unset;
  row-gap: unset;
  scale: unset;
  scroll-behavior: unset;
  scroll-margin-block-end: unset;
  scroll-margin-block-start: unset;
  scroll-margin-bottom: unset;
  scroll-margin-inline-end: unset;
  scroll-margin-inline-start: unset;
  scroll-margin-left: unset;
  scroll-margin-right: unset;
  scroll-margin-top: unset;
  scroll-padding-block-end: unset;
  scroll-padding-block-start: unset;
  scroll-padding-bottom: unset;
  scroll-padding-inline-end: unset;
  scroll-padding-inline-start: unset;
  scroll-padding-left: unset;
  scroll-padding-right: unset;
  scroll-padding-top: unset;
  scroll-snap-align: unset;
  scroll-snap-stop: unset;
  scroll-snap-type: unset;
  shape-image-threshold: unset;
  shape-margin: unset;
  shape-outside: unset;
  shape-rendering: unset;
  size: unset;
  speak-as: unset;
  stop-color: unset;
  stop-opacity: unset;
  suffix: unset;
  symbols: unset;
  system: unset;
  touch-action: unset;
  translate: unset;
  unicode-range: unset;
  widows: unset;
  will-change: unset;
}
</style>
