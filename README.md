# Odin-loops
Loops exercise

- prior to diving into the loop exercise, learn a bit about DOM manipulation

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

## Moving and Removing Nodes

- If you want to move a specific element to a different position on the html document, use `node.appendChild(element to be moved)`
- This will not create a second copy.

- To remove a node, and you know the parent, use `node.removeChild(element to be removed)`.
- When removing a node based only on a reference to itself, use `element.remove()`.
  - This is not supported in older browsers. In that case, use `element.parentNode.removeChild(element)`.

## Manipulating styles

- You can use inline styling by adding `HTMLElement.style` property directly in JS.
- For example `para.style.backgroundColor = "white";`
- Note that when applying inline styling in JS, you need to use lower camelCase, whereas in CSS, you would use hyphenated property names.
- Also note that the values are enclosed in quotes.

- Another common way to manipulate CSS is by adding a `<style>` element to the `<head>` section of the HTML document.
  
```HTML
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple DOM example</title>
    <style>
      .highlight {
        color: white;
        background-color: black;
        padding: 10px;
        width: 250px;
        text-align: center;
      }
    </style>
  </head>
  ```

- Then, use `element.setAttribute()` which takes two arguments
  - the attribute to be set on the element
  - the value you want to set it to.

```js
para.setAttribute("class", "highlight");
```

- The above line will set the values stored in `class` of `highlight` and apply it to the `para` element.

## Some things to take away from the shopping list exercise

- name const variables so that they are self explanatory.

- `.focus()` in simple terms, focuses the cursor back to the input field so that it is not required to manually click on the input field again to make an entry.

- `.addEventListener("click", () => {...})` function adds an action to be executed when (typically) a button is clicked.

## Some things to take away from loops exercises

Loops1

- Use 'for...of' loop whenever possible for simplicity.

Loops2

- `break` statement should be included INSIDE the `if` statement to terminate loop when a match is found.
- CALL the function after the function is written to actually execute it to be displayed on the browser page.

Loops3

```js
  <script>
    let i = 500;
    const para = document.createElement('p');

    function isPrime(num) {
      for(let i = 2; i < num; i++) {
        if(num % i === 0) {
          return false;
        }
      }

      return true;
    }


    // Initially tried the following

    while (i > 1) {
      isPrime(i);  // call the function. This will only call the function, but not do anything else. It will not proceed to the if statement.
      if (isPrime(i) === true) { // Wanted to check if the number passed returns 'true'. But this is not the proper way to check
        para.textContent = `${i}, `; // If I just do 'para.textContent = `${i}, `;', it will not concatenate the recurring results.
                                     // it will only log the final result, which would be '2'.
      }
      i--;
    }

    // remove trailing separator
    para.textContent = para.textContent.slice(0, -2);
    
    // Don't edit the code below here!
    const section = document.querySelector('section');
    section.appendChild(para);
  </script>
  ```

- The fixed code is below.

```js
while (i < 1) {
  if (isPrime(i)) {   // There is no need to call the function on its own, nor does it require comparison against 'true'
                      // if the value of 'isPrime()' when called in the 'if' statement is 'true', it will proceed to execute the code.
    para.textContent = `${i}, `;
  }
  i--;
}

## Notes on Loops from javaScript.info

### While loop evaluates and converts condition to boolean value

- Any expression or variable can be a loop condition (not just comparisons).
- In other words, the `while` loop evaluates and converts the condition to a boolean value.
- For example, `while (i != 0)` can also be written as `while(i)`.
  - If the condition `(i)` becomes `0`, or a `false` boolean value, it will terminate the loop.


### Omit curly braces for single statement loop body

- If the loop body (code to execute) has a single statement, the curly braces can be omitted.

```js
let i = 3;
while(i) alert(i--);
```

- Although this makes the code simpler to write, I personally prefer including curly braces for easier reading and consistency.