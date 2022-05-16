<template>
  <fieldset>
    <label
      v-if="label"
      for="input"
    >
      {{ label }}
    </label>
    <input
      id="input"
      :value="modelValue"
      :placeholder="placeholder"
      @input="handleInput"
    />
  </fieldset>
</template>

<script
  setup
  lang="ts"
>
defineProps({
  modelValue: {
    type: String,
    required: true,
  },
  label: {
    type: String,
    default: '',
  },
  placeholder: {
    type: String,
    default: '',
  },
});

const emit = defineEmits(['update:modelValue']);

function handleInput(e: Event): void {
  const value = (e.target as HTMLInputElement).value;
  emit('update:modelValue', value);
}
</script>

<style scoped>
fieldset {
  all: unset;
  display: flex;
  align-items: center;
  gap: 20px;
}

label {
  all: unset;
  flex: 1;
  color: #540502;
  font-size: 15px;
  text-align: right;
  cursor: default;
}

input {
  all: unset;
  display: inline-flex;
  flex: 2;
  flex-basis: 0%;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 35px;
  padding: 0 10px;
  border-radius: 4px;
  box-shadow: #c99894 0 0 0 1px;
  color: #540502;
  font-size: 15px;
  line-height: 1;
}

input:focus {
  box-shadow: #c99894 0 0 0 2px;
}
</style>
