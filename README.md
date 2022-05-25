# Brickwork

Customizable and accessible UI components with sane defaults for Vue 3.

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
<Button class="btn">
  Click me
</Button>
```

Then, add a property for that class:

```css
.btn {
  --color: tomato;
}
```

In most cases, styling props follow `--{property_name}-{component_part}-{component_state}`.

>Note: it's possible to pass CSS variables that you defined globally, just make sure that there's no naming conflict. For example, this will not work: `--color: var(--color)`.

## Components

### Button

* Emits
  * **@click**: fires on button click
* Slots
  * **default**: button label
* Styling props
  * **--padding**: button content padding
  * **--border-radius**: button border radius
  * **--background**: button background color
  * **--box-shadow**: button box shadow
  * **--color**: button label color
  * **--font-size**: button label font size
  * **--font-weight**: button label font weight
  * **--background-hover**: button background color on hover
  * **--box-shadow-hover**: button box shadow on hover

### Checkbox

* Model
  * **v-model**: checkbox state
* Props
  * **:label**: [optional] checkbox label
* Styling props
  * **--gap**: gap between checkbox and label
  * **--size-check**: height and width of the checkbox
  * **--border-radius-check**: checkbox border radius
  * **--background-check**: checkbox background color
  * **--box-shadow-check**: checkbox box shadow
  * **--color-check**: checkbox color
  * **--color-label**: label color
  * **--font-size-label**: label font size
  * **--font-weight-label**: label font weight

### Dialog

* Props
  * **:isOpen**: whether model is open
* Emits
  * **@close**: fires on model close
* Slots
  * **default**: dialog content
* Styling props
  * **--background-backdrop**: backdrop background color
  * **--padding**: modal content padding
  * **--border-radius**: modal panel border radius
  * **--background**: modal panel background

### Input

* Model
  * **v-model**: input state
* Props
  * **:label**: [optional] input label
  * **:placeholder**: [optional] input placeholder
* Styling props
  * **--flex-direction**: flex direction of label and input
  * **--align-items**: align label and input
  * **--gap**: gap between label and input
  * **--flex-label**: label flex size
  * **--color-label**: label color
  * **--font-size-label**: label font size
  * **--font-weight-label**: label font weight
  * **--flex-input**: input flex size
  * **--padding-input**: input padding
  * **--border-input**: input border
  * **--border-radius-input**: input border radius
  * **--background-input**: input background
  * **--color-input**: input color
  * **--font-size-input**: input font size
  * **--font-weight-input**: input font weight
  * **--border-input-focus**: input border on focus

### RadioGroup

* Model
  * **v-model**: selected option
* Props
  * **:options**: list of available options
* Styling props
  * **--gap**: gap between items
  * **--gap-item**: gap between radio button and label
  * **--size-radio**: height and width of the radio button
  * **--border-radius-radio**: radio button border radius
  * **--background-radio**: radio button background color
  * **--box-shadow-radio**: radio button box shadow
  * **--size-radio-indicator**: height and width of the radio indicator
  * **--border-radius-radio-indicator**: radio indicator border radius
  * **--color-radio-indicator**: radio indicator color
  * **--color-label**: label color
  * **--font-size-label**: label font size
  * **--font-weight-label**: label font weight

### Select

* Model
  * **v-model**: selected option
* Props
  * **:options**: list of available options
* Slots
  * **#trigger** trigger element
* Styling props
  * **--padding-trigger**: trigger content padding
  * **--border-trigger**: trigger border
  * **--border-radius-trigger**: trigger border radius
  * **--background-trigger**: trigger background color
  * **--box-shadow-trigger**: trigger box shadow
  * **--color-trigger**: trigger color
  * **--font-size-trigger**: trigger font size
  * **--font-weight-trigger**: trigger font weight
  * **--background-trigger-hover**: trigger background color on hover
  * **--border-trigger-focus**: trigger border on focus
  * **--padding-list**: option list padding
  * **--border-radius-list**: option list border radius
  * **--background-list**: option list background color
  * **--box-shadow-list**: option list box shadow
  * **--padding-item**: item padding
  * **--gap-item**: item gap
  * **--border-radius-item**: item border radius
  * **--color-item**: item color
  * **--font-size-item**: item font size
  * **--font-weight-item**: item font weight
  * **--background-item-active**: active item background color
  * **--color-item-active**: active item color
