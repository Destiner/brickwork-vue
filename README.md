# Brickwork

_Unstyled Vue 3 UI components for your design system._

Brickwork is a set of unstyled, accessible components to be used as a baseline for your custom UI kit. Brickwork handles all the low-level plumbing so you can focus on look and feel. No more figuring out how to make a custom checkbox!

Currently, following components are available:

- Button
- Checkbox
- Switch
- Dialog
- Input
- RadioGroup
- Select
- Dropdown
- Accordion
- Tabs (_soon_)
- Popover (_soon_)

## Demo

See [showcase](https://brickwork-showcase.netlify.app) ([source code](./examples/showcase)) featuring some of the customizations possible.

## Installation

First, add the package to your project:

```bash
npm i brickwork-vue
```

Then, import the necessary styles in your main Vue component (e.g. `App.vue`):

```js
import 'brickwork-vue/style.css';
```

## Customization

All custom styles applied via CSS custom properties (variables). For example to change the color of the button label, first add a class to the component in the template:

```html
<button class="btn">Click me</button>
```

Then, add a property for that class:

```css
.btn {
  --color: tomato;
}
```

In most cases, styling props follow `--{property_name}-{component_part}-{component_state}`.

> Note: it's possible to pass CSS variables that you defined globally, just make sure that there's no naming conflict. For example, this will not work: `--color: var(--color)`.

## Components

### Button

- Emits
  - **@click**: fires on button click
- Slots
  - **default**: button label
- Styling props
  - **--padding**: button content padding
  - **--border**: button border
  - **--border-radius**: button border radius
  - **--background**: button background color
  - **--box-shadow**: button box shadow
  - **--color**: button label color
  - **--font-size**: button label font size
  - **--font-weight**: button label font weight
  - **--line-height**: button label line height
  - **--border-hover**: button border on hover
  - **--background-hover**: button background color on hover
  - **--box-shadow-hover**: button box shadow on hover
  - **--color-hover**: button label color on hover
  - **--background-disabled**: button background on disabled
  - **--color-disabled**: button label color on disabled

### Checkbox

- Model
  - **v-model**: checkbox state
- Props
  - **:label**: [optional] checkbox label
- Styling props
  - **--gap**: gap between checkbox and label
  - **--size-check**: height and width of the checkbox
  - **--border-check**: checkbox border
  - **--border-radius-check**: checkbox border radius
  - **--background-check**: checkbox background color
  - **--box-shadow-check**: checkbox box shadow
  - **--color-check**: checkbox color
  - **--color-label**: label color
  - **--font-size-label**: label font size
  - **--font-weight-label**: label font weight

### Switch

- Model
  - **v-model**: switch state
- Props
  - **:label**: [optional] switch label
- Styling props
  - **--width**: switch width
  - **--height**: switch height
  - **--background**: switch background
  - **--box-shadow**: switch box shadow
  - **--background-hover**: switch background on hover
  - **--size-thumb**: switch thumb width and height
  - **--color-thumb**: switch thumb color
  - **--box-shadow-thumb**: switch thumb box shadow

### Dialog

- Props
  - **:isOpen**: whether model is open
- Emits
  - **@close**: fires on model close
- Slots
  - **default**: dialog content

### Input

- Model
  - **v-model**: input state
- Props
  - **:label**: [optional] input label
  - **:placeholder**: [optional] input placeholder
- Emits
  - **@init**: fires on input init, provides reference to input element
- Styling props
  - **--flex-direction**: flex direction of label and input
  - **--align-items**: align label and input
  - **--gap**: gap between label and input
  - **--flex-label**: label flex size
  - **--color-label**: label color
  - **--font-size-label**: label font size
  - **--font-weight-label**: label font weight
  - **--flex-input**: input flex size
  - **--padding-input**: input padding
  - **--border-input**: input border
  - **--border-radius-input**: input border radius
  - **--background-input**: input background
  - **--color-input**: input color
  - **--font-size-input**: input font size
  - **--font-weight-input**: input font weight
  - **--line-height-input**: input line height
  - **--border-input-focus**: input border on focus
  - **--background-input-focus**: input background on focus

### RadioGroup

- Model
  - **v-model**: selected option
- Props
  - **:options**: list of available options
- Styling props
  - **--gap**: gap between items
  - **--gap-item**: gap between radio button and label
  - **--size-radio**: height and width of the radio button
  - **--border-radio**: radio button border
  - **--border-radius-radio**: radio button border radius
  - **--background-radio**: radio button background color
  - **--box-shadow-radio**: radio button box shadow
  - **--size-radio-indicator**: height and width of the radio indicator
  - **--border-radius-radio-indicator**: radio indicator border radius
  - **--color-radio-indicator**: radio indicator color
  - **--color-label**: label color
  - **--font-size-label**: label font size
  - **--font-weight-label**: label font weight
  - **--line-height-label**: label line height

### Select

- Model
  - **v-model**: selected option
- Props
  - **:options**: list of available options
- Slots
  - **#trigger** trigger element
- Styling props
  - **--gap**: gap between trigger and option list
  - **--gap-trigger**: gap between label and trigger button
  - **--flex-direction-trigger**: flex direction of label and trigger button
  - **--align-items-trigger**: align label and trigger button
  - **--flex-label**: label flex
  - **--color-label**: label color
  - **--font-size-label**: label font size
  - **--font-weight-label**: label font weight
  - **--flex-button**: trigger button flex
  - **--padding-button**: trigger button content padding
  - **--border-button**: trigger button border
  - **--border-radius-button**: trigger button border radius
  - **--background-button**: trigger button background color
  - **--box-shadow-button**: trigger button box shadow
  - **--color-button**: trigger button color
  - **--font-size-button**: trigger button font size
  - **--font-weight-button**: trigger button font weight
  - **--line-height-button**: trigger button line height
  - **--background-button-hover**: trigger button background color on hover
  - **--box-shadow-button-hover**: trigger button box shadow on hover
  - **--border-button-focus**: trigger button border on focus
  - **--padding-list**: option list padding
  - **--border-list**: option list border
  - **--border-radius-list**: option list border radius
  - **--background-list**: option list background color
  - **--box-shadow-list**: option list box shadow
  - **--padding-item**: item padding
  - **--gap-item**: item gap
  - **--border-radius-item**: item border radius
  - **--color-item**: item color
  - **--font-size-item**: item font size
  - **--font-weight-item**: item font weight
  - **--line-height-item**: item line height
  - **--background-item-active**: active item background color
  - **--color-item-active**: active item color
  - **--size-item-active-icon**: active item icon size

### Dropdown

- Props
  - **:options**: list of available options
- Emits
  - **@select**: fires on option select
- Slots
  - **#trigger** trigger element
- Styling props
  - **--gap**: gap between trigger and option list
  - **--flex-button**: trigger button flex
  - **--padding-button**: trigger button content padding
  - **--border-button**: trigger button border
  - **--border-radius-button**: trigger button border radius
  - **--background-button**: trigger button background color
  - **--box-shadow-button**: trigger button box shadow
  - **--color-button**: trigger button color
  - **--font-size-button**: trigger button font size
  - **--font-weight-button**: trigger button font weight
  - **--line-height-button**: trigger button line height
  - **--background-button-hover**: trigger button background color on hover
  - **--box-shadow-button-hover**: trigger button box shadow on hover
  - **--border-button-focus**: trigger button border on focus
  - **--padding-list**: option list padding
  - **--border-list**: option list border
  - **--border-radius-list**: option list border radius
  - **--background-list**: option list background color
  - **--box-shadow-list**: option list box shadow
  - **--padding-item**: item padding
  - **--gap-item**: item gap
  - **--border-radius-item**: item border radius
  - **--color-item**: item color
  - **--font-size-item**: item font size
  - **--font-weight-item**: item font weight
  - **--line-height-item**: item line height
  - **--background-item-active**: active item background color
  - **--color-item-active**: active item color

### Accordion

- Props
  - **:items**: list of displayed items
- Styling props
  - **--gap**: gap between items
  - **--padding**: wrapper padding
  - **--border-radius**: wrapper border radius
  - **--background**: wrapper background
  - **--height-divider**: item divider vertial size
  - **--background-divider**: item divider color
  - **--padding-button**: button padding
  - **--border-radius-button**: button border radius
  - **--background-button**: button background
  - **--color-button**: button color
  - **--font-size-button**: button font size
  - **--background-button-hover**: button background on hover
  - **--padding-panel**: content panel padding
  - **--background-panel**: content panel background
  - **--color-panel**: content panel color
  - **--font-size-panel**: content panel font size
