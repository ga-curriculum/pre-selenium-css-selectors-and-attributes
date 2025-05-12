<h1>
  <span class="headline">Pre-Selenium: CSS Selectors and Attributes</span>
  <span class="subhead">Advanced Selector Combinations</span>
</h1>

**Learning objective:** Use compound and descendant selectors to target elements within specific structures (such as buttons inside a form).

## Combining multiple selectors for more precise targeting

In earlier lessons, you learned how to use simple CSS selectors—like targeting an element by its tag name, class, or id—to pick out elements on a web page. However, most real web pages present more complex structures. Elements are often nested within other elements, appear in repeated groups, or share similar attributes with many siblings on the same page.

To navigate these challenges confidently during test automation, you will need advanced selector combinations. With these tools, you can precisely target elements in the context of their parent, siblings, or by blending multiple requirements together.

**Compound selectors** allow you to combine two or more simple selectors so that _all_ the conditions must be true for an element to be selected. This makes your selectors reliable, easier to read, and less likely to break if the page structure shifts.

### Example: Combining class and attribute

```css
button.primary[type="submit"]
```

This selector matches any `<button>` element that has both the class `primary` and a `type` attribute set to `submit`. Both conditions are required.

> 🏆 Best practice: Relying on compound selectors reduces the chance of accidentally automating the wrong button—especially on pages with many similar buttons.

## Descendant selectors: How to target nested elements within a parent

A frequent goal in UI automation is to find elements _nested_ inside a specific container. For example, finding all the buttons _inside_ a particular form or all links within a navigation section.

**Descendant selectors** make this easy. They allow you to select elements that appear anywhere inside a parent—or ancestor—element, no matter how deeply nested.

**Syntax:**

```css
parent child
```

- _parent_ can be an element, class, or id selector.
- _child_ is the element you want to find within that parent’s subtree.

### Buttons inside a form

```css
form button
```

This matches any `<button>` element located within any `<form>`, even if there are other elements in between.

#### Scenario

Suppose you have this HTML:

```html
<form id="signup-form">
  <div class="fieldset">
    <button type="submit">Sign Up</button>
  </div>
</form>
```

- The selector `form button` highlights the "Sign Up" button, even though there is a `<div>` between it and the `<form>`.

For greater precision, you can use the form’s id:

```css
#signup-form button;
```

Now, only buttons inside the form with `id="signup-form"` will be selected.

> 🧠 When you want to automate actions only within a particular section or form, descendant selectors help you avoid picking up elements that look similar but are in the wrong context.

## Child selectors: Differentiating direct parent-child relationships

Sometimes, only the direct children of a parent are relevant for your automation or test. You may wish to avoid selecting elements that are inside other containers, even if they are ultimately contained within your parent element.

**Child selectors** help with this by using the `>` combinator.

**Syntax:**

```css
parent > child
```

This matches `child` elements that are immediate children of `parent`—not grandchildren or deeper descendants.

### Direct buttons inside a form

```css
form > button
```

This matches any `<button>` that is a _direct_ child of a `<form>`, but will not match a button inside an embedded `<div>`.

#### Visual breakdown

Here’s an example:

```html
<form>
  <button>Direct Child</button>
  <div>
    <button>Nested Child</button>
  </div>
</form>
```

- The selector `form > button` matches only “Direct Child.”
- The selector `form button` would match both “Direct Child” and “Nested Child.”

> ⚠ Use child selectors for extra accuracy when your page structure is known and consistent, to prevent accidental selection of unwanted elements.

## Sibling selectors: Using adjacent and general sibling approaches

Not all elements you need to select have a parent-child relationship. Some are siblings—elements that share the same parent and appear next to each other.

**Two types of sibling selectors:**

1. **Adjacent sibling (`+`)**: Matches the very next sibling.
2. **General sibling (`~`)**: Matches all siblings after a certain element.

### Adjacent sibling

```css
label + input
```

Selects the first `<input>` that immediately follows a `<label>`.

### General sibling

```css
label ~ input
```

Matches all `<input>` elements that appear after any `<label>` with the same parent, not necessarily right away.

#### Scenario

Suppose you have:

```html
<label for="search">Search</label>
<input id="search" type="text" />
<input type="submit" value="Go" />
```

- The selector `label + input` matches only the text input that directly follows the label.
- The selector `label ~ input` matches both the text input and the "Go" button.

> 🧠 In form automation, sibling selectors are useful for selecting fields closely related in layout, such as pairing a label and its input or checking for errors displayed next to a field.

<div class="activity guided-walkthrough">
  <h2 class="title">Applying advanced selectors to navigate complex DOM structures</h2>
  <span class="minutes">5 min</span>
</div>

Let’s connect these advanced CSS selectors to common automation challenges. These examples are relevant for test scripts and UI automation—especially as you start to “speak the language of the browser.”

### Scenario 1: Find all “Remove” buttons inside shopping cart items

```html
<div class="cart-item">
  <span class="item-title">Laptop</span>
  <button class="danger remove-btn">Remove</button>
</div>
```

Selector:

```css
.cart-item .remove-btn;
```

- This targets every `.remove-btn` inside an element with class `cart-item`.

### Scenario 2: Target only the first link in a navigation bar

```html
<nav>
  <a href="/home">Home</a>
  <a href="/products">Products</a>
</nav>
```

Selector:

```css
nav > a
```

- This selects only `<a>` elements that are immediate children of `<nav>`.

### Scenario 3: Select checkboxes that follow a label

```html
<label for="opt-in">Subscribe to emails</label>
<input type="checkbox" id="opt-in" />

<label>Accept terms</label>
<input type="checkbox" />
```

Selector:

```css
label + input[type="checkbox"]
```

- Selects a checkbox input that comes immediately after a label.

### Scenario 4: Links inside a specific section (using IDs)

```html
<section id="main-content">
  <a href="/overview">Overview</a>
  <a href="/pricing">Pricing</a>
</section>
```

Selector:

```css
#main-content a;
```

- Matches all `<a>` links inside the section with id `main-content`.

### Scenario 5: Combining attribute, class, and combinator selectors

```html
<div class="filters">
  <input type="checkbox" name="promo-only" />
  <label for="promo-only">Promo Only</label>
</div>
```

Selector:

```css
.filters input[type='checkbox'];
```

- Precisely selects any checkbox input inside the `.filters` container.

> 💡 These selector patterns mimic how you might approach elements in a complex spreadsheet: first narrowing by section, then by type or purpose, ensuring you interact only with relevant data.

## Knowledge check

❓ Which selector would match only button elements that are direct children of a form (not nested in any other element inside the form)?

- A. `form button`
- B. `form > button`
- C. `form .button`
- D. `form [type="button"]`

❓ What does the selector `label + input[type="checkbox"]` select?

- A. Any input with type checkbox inside a label
- B. All checkboxes on the page
- C. Any checkbox input that comes immediately after a label
- D. Any label followed by at least one input

## Reflect

- Did you discover new combinations or approaches for targeting complex elements?
- Which selectors might be fragile—breaking if the layout changes—and which ones seem robust?
