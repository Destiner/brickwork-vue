<template>
  <div class="view">
    <h1>Showcase</h1>
    <div class="component">
      <h2>Button</h2>
      <div class="items">
        <div class="item button-a">
          <Button @click="handleButtonClick"> Click me </Button>
        </div>
        <div class="item button-b">
          <Button @click="handleButtonClick"> Click me </Button>
        </div>
        <div class="item button-c">
          <Button @click="handleButtonClick"> Click me </Button>
        </div>
      </div>
    </div>
    <div class="component">
      <h2>Input</h2>
      <div class="items items-vertical">
        <div class="item input-a">
          <Input
            v-model="inputValue"
            :label="'Email'"
            :placeholder="'tim@apple.com'"
          />
        </div>
        <div class="item input-b">
          <Input
            v-model="inputValue"
            :placeholder="'tim@apple.com'"
          />
        </div>
        <div class="item input-c">
          <Input
            v-model="inputValue"
            :label="'Email'"
            :placeholder="'tim@apple.com'"
          />
        </div>
      </div>
    </div>
    <div class="component">
      <h2>Checkbox</h2>
      <div class="items">
        <div class="item checkbox-a">
          <Checkbox
            v-model="checkboxValue"
            :label="'Agree'"
          />
        </div>
        <div class="item checkbox-b">
          <Checkbox
            v-model="checkboxValue"
            :label="'Agree'"
          />
        </div>
        <div class="item checkbox-c">
          <Checkbox
            v-model="checkboxValue"
            :label="'Agree'"
          />
        </div>
      </div>
    </div>
    <div class="component">
      <h2>Radio Group</h2>
      <div class="items">
        <div class="item radio-group-a">
          <RadioGroup
            v-model="radioOption"
            :options="radioOptions"
          />
        </div>
        <div class="item radio-group-b">
          <RadioGroup
            v-model="radioOption"
            :options="radioOptions"
          />
        </div>
        <div class="item radio-group-c">
          <RadioGroup
            v-model="radioOption"
            :options="radioOptions"
          />
        </div>
      </div>
    </div>
    <div class="component">
      <h2>Select</h2>
      <div class="items">
        <div class="item select-a">
          <Select
            v-model="selectOption"
            :options="selectOptions"
          >
            <template #trigger="{ selectedItem }">
              <span>{{ selectedItem.label }}</span>
            </template>
          </Select>
        </div>
        <div class="item select-b">
          <Select
            v-model="selectOption"
            :options="selectOptions"
          >
            <template #trigger="{ selectedItem }">
              <span>{{ selectedItem.label }}</span>
            </template>
          </Select>
        </div>
        <div class="item select-c">
          <Select
            v-model="selectOption"
            :options="selectOptions"
          >
            <template #trigger="{ selectedItem }">
              <span>{{ selectedItem.label }}</span>
            </template>
          </Select>
        </div>
      </div>
    </div>
    <div class="component">
      <h2>Dialog</h2>
      <div class="items">
        <div class="item">
          <Button
            class="button-a"
            @click="openDialogA"
          >
            Open dialog
          </Button>
          <Dialog
            :is-open="isDialogAOpen"
            class="dialog-a"
            @close="closeDialogA"
          >
            <div class="dialog-content-a">
              <h1>Constantinople</h1>
              <div>
                The capital of the Roman/Byzantine Empire, the Latin Empire, and
                the Ottoman Empire. The capital then moved to Ankara following
                the Turkish War of Independence. Officially renamed Istanbul in
                1930, the city is today the largest city and financial centre of
                the Republic of Turkey. It remains the largest city in Europe.
              </div>
            </div>
          </Dialog>
        </div>
        <div class="item">
          <Button
            class="button-b"
            @click="openDialogB"
          >
            Open dialog
          </Button>
          <Dialog
            :is-open="isDialogBOpen"
            class="dialog-b"
            @close="closeDialogB"
          >
            <div class="dialog-content-b">
              <h1>Constantinople</h1>
              <div>
                The capital of the Roman/Byzantine Empire, the Latin Empire, and
                the Ottoman Empire. The capital then moved to Ankara following
                the Turkish War of Independence. Officially renamed Istanbul in
                1930, the city is today the largest city and financial centre of
                the Republic of Turkey. It remains the largest city in Europe.
              </div>
            </div>
          </Dialog>
        </div>
        <div class="item">
          <Button
            class="button-c"
            @click="openDialogC"
          >
            Open dialog
          </Button>
          <Dialog
            :is-open="isDialogCOpen"
            class="dialog-c"
            @close="closeDialogC"
          >
            <div class="dialog-content-c">
              <h1>Constantinople</h1>
              <div>
                The capital of the Roman/Byzantine Empire, the Latin Empire, and
                the Ottoman Empire. The capital then moved to Ankara following
                the Turkish War of Independence. Officially renamed Istanbul in
                1930, the city is today the largest city and financial centre of
                the Republic of Turkey. It remains the largest city in Europe.
              </div>
            </div>
          </Dialog>
        </div>
      </div>
    </div>
  </div>
</template>

<script
  setup
  lang="ts"
>
import {
  Button,
  Checkbox,
  Dialog,
  Input,
  RadioGroup,
  Select,
} from 'brickwork-vue';
// eslint-disable-next-line import/no-unresolved
import 'brickwork-vue/style.css';
import { ref } from 'vue';

const inputValue = ref('');
const checkboxValue = ref(true);

const radioOption = ref('apple');
const radioOptions = [
  {
    label: 'Apple',
    value: 'apple',
  },
  {
    label: 'Pear',
    value: 'pear',
  },
  {
    label: 'Grapes',
    value: 'grapes',
  },
];

const selectOption = ref('mars');
const selectOptions = [
  {
    label: 'Mars',
    value: 'mars',
  },
  {
    label: 'Venera',
    value: 'venera',
  },
  {
    label: 'Saturn',
    value: 'saturn',
  },
  {
    label: 'Neptune',
    value: 'neptune',
  },
];

const isDialogAOpen = ref(false);
const isDialogBOpen = ref(false);
const isDialogCOpen = ref(false);

function openDialogA(): void {
  isDialogAOpen.value = true;
}

function openDialogB(): void {
  isDialogBOpen.value = true;
}

function openDialogC(): void {
  isDialogCOpen.value = true;
}

function closeDialogA(): void {
  isDialogAOpen.value = false;
}

function closeDialogB(): void {
  isDialogBOpen.value = false;
}

function closeDialogC(): void {
  isDialogCOpen.value = false;
}

function handleButtonClick(): void {
  console.log(inputValue.value);
}
</script>

<style>
body {
  margin: 16px 16px 64px;
  color: #2c3e50;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

h1,
h2 {
  margin: 8px 0;
}

.view {
  display: flex;
  flex-direction: column;
  max-width: 800px;
  gap: 16px;
}

.items {
  display: flex;
  gap: 32px;
}

.items-vertical {
  flex-direction: column;
}

.item {
  max-width: 200px;
  text-align: start;
}

.button-b {
  --background: tomato;
  --background-hover: tomato;
  --border-radius: 16px;
  --box-shadow: none;
  --box-shadow-hover: #e65940c0 0 2px 10px;
  --color: white;
}

.button-c {
  --background: black;
  --background-hover: #222;
  --color: white;
  --border-radius: 0;
  --box-shadow: none;
  --box-shadow-hover: none;
}

.input-b {
  --color-label: tomato;
  --border-input: 2px solid #ff6347c0;
  --border-radius-input: 8px;
  --background-input: #fff6f5;
  --background-input-focus: #ffedeb;
  --color-input: tomato;
  --font-weight-input: 500;
  --border-input-focus: 2px solid #ff6347;
}

.input-c {
  --flex-direction: row;
  --align-items: center;
  --gap: 8px;
  --color-label: black;
  --border-input: 1px solid black;
  --border-radius-input: 0;
  --color-input: black;
  --font-weight-input: 400;
  --border-input-focus: 1px solid black;
}

.checkbox-b {
  --gap: 20px;
  --border-radius-check: 20%;
  --background-check: #ffe9e6;
  --box-shadow-check: #e6594040 0 2px 4px;
  --color-check: tomato;
  --color-label: tomato;
  --font-weight-label: 500;
}

.checkbox-c {
  --gap: 8px;
  --border-check: 1px solid black;
  --background-check: white;
  --box-shadow-check: none;
  --color-check: black;
  --color-label: black;
  --font-weight-label: 400;
}

.radio-group-b {
  --gap-item: 20px;
  --background-radio: #ffe9e6;
  --box-shadow-radio: #e6594040 0 2px 4px;
  --size-radio-indicator: 12px;
  --color-radio-indicator: tomato;
  --color-label: tomato;
  --font-weight-label: 500;
}

.radio-group-c {
  --gap-item: 8px;
  --background-radio: white;
  --border-radio: 1px solid black;
  --box-shadow-radio: none;
  --size-radio-indicator: 8px;
  --color-radio-indicator: black;
  --color-label: black;
  --font-weight-label: 400;
}

.select-b {
  --gap: 8px;
  --border-button: 2px solid transparent;
  --border-radius-button: 8px;
  --background-button: tomato;
  --box-shadow-button: none;
  --color-button: white;
  --font-weight-button: 500;
  --background-button-hover: tomato;
  --box-shadow-button-hover: #e65940c0 0 2px 10px;
  --border-button-focus: 2px solid black;
  --padding-list: 8px;
  --border-list: 4px solid tomato;
  --border-radius-list: 16px;
  --background-list: white;
  --padding-item: 2px 8px;
  --gap-item: 8px;
  --border-radius-item: 4px;
  --color-item: tomato;
  --font-size-item: 12px;
  --font-weight-item: 400;
  --background-item-active: tomato;
  --color-item-active: white;
  --size-item-active-icon: 20px;
}

.select-c {
  --gap: 4px;
  --border-button: 1px solid black;
  --border-radius-button: 0;
  --background-button: black;
  --box-shadow-button: none;
  --color-button: white;
  --font-weight-button: 400;
  --background-button-hover: #222;
  --box-shadow-button-hover: none;
  --border-button-focus: 1px solid #222;
  --padding-list: 4px;
  --border-list: 1px solid black;
  --border-radius-list: 0;
  --background-list: white;
  --box-shadow-list: none;
  --padding-item: 2px 4px;
  --gap-item: 2px;
  --border-radius-item: 0;
  --color-item: black;
  --font-size-item: 12px;
  --font-weight-item: 400;
  --background-item-active: black;
  --color-item-active: white;
  --size-item-active-icon: 10px;
}

.dialog-b {
  --background-backdrop: #e6594060;
  --padding: 32px;
  --border-radius: 24px;
  --background: #fff6f5;
}

.dialog-c {
  --padding: 8px;
  --border-radius: 0;
  --background: white;
}
</style>
