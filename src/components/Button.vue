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
  height: 35px;
  padding: 0 15px;
  border-radius: 4px;
  background: #fafafa;
  box-shadow: #00000024 0 2px 10px;
  color: #540502;
  font-size: 15px;
  font-weight: 500;
  line-height: 1;
}

button:focus {
  box-shadow: #290402 0 0 0 2px;
}

button:hover {
  background-color: #eee;
}
</style>
