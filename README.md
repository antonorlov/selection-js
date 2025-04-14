# Selection-js

A lightweight JavaScript library that creates customizable tooltip menus when users select text on your website.

## Demo

See the [live demo](https://antonorlov.github.io/selection-js/)

## Features

- Creates a tooltip menu over selected text
- Customizable appearance and behavior
- Works in input fields and textareas
- No dependencies

## Installation

Include the script directly in your HTML:

```html
<script src="https://cdn.jsdelivr.net/gh/antonorlov/selection-js/selection.js"></script>
```

Or download and include it locally:

```html
<script src="path/to/selection.js"></script>
```

## Basic Usage

```javascript
// Create a new instance
const selection = new Selection();

// Configure and initialize
selection.config({
  menu: [
    {
      innerHTML: 'Copy',
      cb: (text) => {
        Selection().copyTextToClipboard(text);
        alert(`Copied: "${text}"`);
      }
    },
    {
      innerHTML: 'Share',
      cb: (text) => alert(`Share: "${text}"`)
    }
  ],
  rootElement: document.querySelector('.my-content')
}).init();
```

## Configuration Options

| Option | Type | Description |
|--------|------|-------------|
| `menu` | Array | An array of menu items with `innerHTML` and `cb` (callback) properties |
| `rootElement` | DOM Element | The element to apply selection.js to (defaults to window) |
| `backgroundColor` | String | Custom background color for the tooltip (e.g., '#4CAF50') |
| `iconColor` | String | Custom color for icons and text in the tooltip (e.g., '#ffffff') |
| `disable` | Boolean | Disable the tooltip arrow when set to true |

### Menu Items

Each menu item in the `menu` array should have:

- `innerHTML`: HTML content for the button (text or HTML/SVG)
- `cb`: Callback function that receives the selected text and DOM node

## Advanced Usage

### Custom Styling

```javascript
selection.config({
  menu: [/* your menu items */],
  backgroundColor: '#673AB7', // Purple background
  iconColor: '#FFEB3B',       // Yellow text/icons
  rootElement: document.querySelector('.content')
}).init();
```

### Multiple Instances

You can create multiple independent instances that work on different parts of your page:

```javascript
// First instance for article content
const textSelection = new Selection();
textSelection.config({
  menu: [/* menu items */],
  rootElement: document.querySelector('.article')
}).init();

// Second instance for input fields
const inputSelection = new Selection();
inputSelection.config({
  menu: [/* different menu items */],
  rootElement: document.querySelector('.form')
}).init();
```

### Using SVG Icons

```javascript
selection.config({
  menu: [
    {
      innerHTML: '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><path d="M16 1H4c-1.1 0-2 .9-2 2v14h2V3h12V1zm3 4H8c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h11c1.1 0 2-.9 2-2V7c0-1.1-.9-2-2-2zm0 16H8V7h11v14z"/></svg>',
      cb: (text) => Selection().copyTextToClipboard(text)
    }
  ],
  // other options
}).init();
```

## API Methods

### `config(options)`

Sets configuration options for the instance.

### `init()`

Initializes the instance and attaches event listeners.

### `copyTextToClipboard(text)`

Utility function to copy text to clipboard using modern Clipboard API with fallback.

## Browser Compatibility

- Chrome 42+
- Firefox 41+
- Safari 10+
- Edge 12+
- Opera 29+

## License

ISC