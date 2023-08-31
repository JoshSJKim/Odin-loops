# Odin-loops
Loops exercise

## DOM manipulation

- Use `document.querySelector()` to 'grab' specific reference to html elements.
- `node.textContent` allows you to completely edit the text of the currently selected element.
- `node.href` allows you to edit the href value of an anchor element.

- `document.createElement()` creates a specified element in memory in JS environment, but it does not necessarily alter the actual html file.
- In order to alter the html file, use `Node.appendChild(element)` to append the created element in the html document.
- You can also create a new text node by assigning `document.createTextNode("some string")` to a new `const` variable.
- The newly created text node can be appended to an element in the html document by using the `document.querySelector(element)` to select a specific element. 

```js
const text = document.createTextNode(
  " - this is DOM manipulation exercise."
);

const linkPara = document.querySelector("p");
linkPara.appendChild(text);
```

- `document.createTextNode()` creates a new text node, which is assigned to a const variable called "text".
- A new const variable "linkPara" is assigned with `document.querySelector("p")`.
- The text value assigned to `const text` is appended to the element specified in `const linkPara`.

- Note that `document.querySelector("p")` points to the 'p' element that actually exists in the html document.
- If there is a 'p' element that is created using `document.createElement('p')`, `document.querySelector('p')` will not recognize it because it only exists in the JS memory environment.

- There are older methods of grabbing element reference
  - `document.getElementById('id value')`
  - `document.getElementByTagName('tag name')`
- These can still be used, but not as convenient as `document.querySelector()`.

- When using `document.querySelector('p')` for example, and there are multiple 'p' elements, but you need to grab a specific 'p' element, add a class or id attribute to that 'p' element and use the class/id value as the argument in `document.querySelector()`