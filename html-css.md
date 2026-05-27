# HTML and CSS

## Index

1. [Box Model](#box-model)

2. [Inline versus Block Elements](#inline-versus-block-elements)

3. [Positioning: Relative and Absolute](#positioning-relativeabsolute)

4. [Common CSS Structural Classes](#common-css-structural-classes)

5. [Common CSS Styling Classes](#common-css-styling-classes)

6. [CSS Specificity](#css-specificity)

7. [CSS Responsive Queries](#css-responsive-queries)

8. [Flexbox and Grid](#flexbox-and-grid)

## Box Model

Every HTML element on a webpage is treated as a rectangular box. Understanding the box model helps developers control spacing, sizing, alignment, and layout properly.

The box model determines how much space an element occupies on the screen and how its dimensions are calculated.

---

## Components of the Box Model

The CSS box model consists of four main parts:

1. Content
2. Padding
3. Border
4. Margin

```text
+---------------------------+
|         Margin            |
|  +---------------------+  |
|  |      Border         |  |
|  |  +---------------+  |  |
|  |  |    Padding    |  |  |
|  |  | +-----------+ |  |  |
|  |  | |  Content  | |  |  |
|  |  | +-----------+ |  |  |
|  |  +---------------+  |  |
|  +---------------------+  |
+---------------------------+
```

---

## 1. Content

The content area contains the actual text, image, or other media inside the element.

The `width` and `height` properties usually define the size of the content area.

### Example

```html
<div class="box">
  Hello World
</div>
```

```css
.box {
  width: 200px;
  height: 100px;
}
```

Here:

- Width = `200px`
- Height = `100px`

This size applies only to the content area by default.

---

## 2. Padding

Padding is the space between the content and the border.

It creates internal spacing inside the element.

### Example

```css
.box {
  padding: 20px;
}
```

This adds:

- `20px` space on all four sides inside the border.

### Individual Padding Properties

```css
padding-top
padding-right
padding-bottom
padding-left
```

### Shorthand Syntax

```css
padding: 10px 20px 30px 40px;
```

Order:

```text
Top Right Bottom Left
```

---

## 3. Border

The border surrounds the padding and content.

It creates a visible boundary around the element.

### Example

```css
.box {
  border: 2px solid black;
}
```

This means:

- Border width = `2px`
- Border style = `solid`
- Border color = `black`

### Common Border Styles

```text
solid
dashed
dotted
double
groove
ridge
none
```

### Individual Border Properties

```css
border-width
border-style
border-color
```

---

## 4. Margin

Margin is the outer space outside the border.

It creates distance between elements.

### Example

```css
.box {
  margin: 20px;
}
```

This adds `20px` space outside the element on all sides.

### Individual Margin Properties

```css
margin-top
margin-right
margin-bottom
margin-left
```

### Shorthand Syntax

```css
margin: 10px 20px 30px 40px;
```

Order:

```text
Top Right Bottom Left
```

---

## Total Width and Height Calculation

By default, CSS calculates total size like this:

### Total Width

```text
Total Width =
Content Width +
Left Padding +
Right Padding +
Left Border +
Right Border +
Left Margin +
Right Margin
```

### Total Height

```text
Total Height =
Content Height +
Top Padding +
Bottom Padding +
Top Border +
Bottom Border +
Top Margin +
Bottom Margin
```

---

## Example of Actual Size Calculation

```css
.box {
  width: 200px;
  padding: 20px;
  border: 5px solid black;
  margin: 10px;
}
```

### Calculation

```text
Content Width = 200px

Padding Left + Right = 40px
Border Left + Right = 10px
Margin Left + Right = 20px

Total Width = 270px
```

---

## `box-sizing` Property

The `box-sizing` property changes how width and height are calculated.

---

## 1. `content-box` (Default)

```css
box-sizing: content-box;
```

In this mode:

- Width and height apply only to content.
- Padding and border increase total size.

### Example

```css
.box {
  width: 200px;
  padding: 20px;
  border: 5px solid black;
  box-sizing: content-box;
}
```

Actual width becomes:

```text
200 + 40 + 10 = 250px
```

---

## 2. `border-box`

```css
box-sizing: border-box;
```

In this mode:

- Padding and border are included inside the specified width and height.
- Total size remains fixed.

### Example

```css
.box {
  width: 200px;
  padding: 20px;
  border: 5px solid black;
  box-sizing: border-box;
}
```

Actual total width remains:

```text
200px
```

The content area automatically shrinks to fit.

---

## Why `border-box` is Preferred

Most developers use:

```css
* {
  box-sizing: border-box;
}
```

Advantages:

- Easier size calculations
- Predictable layouts

---

## Margin Collapse

Vertical margins between block elements can collapse.

### Example

```html
<div class="box1"></div>
<div class="box2"></div>
```

```css
.box1 {
  margin-bottom: 20px;
}

.box2 {
  margin-top: 30px;
}
```

Expected:

```text
20px + 30px = 50px
```

Actual result:

```text
30px
```

The larger margin wins.

This behavior is called **margin collapsing**.

---

## Auto Margin

`margin: auto` is commonly used for centering elements horizontally.

### Example

```css
.box {
  width: 300px;
  margin: auto;
}
```

This centers the element inside its parent container.

---

## Box Model in Inline Elements

Inline elements behave differently.

Examples:

```html
<span>
<a>
<strong>
```

Characteristics:

- Width and height usually do not apply
- Vertical margin may not work properly
- Padding and borders still appear

---

## Box Model in Block Elements

Block elements fully follow the box model.

Examples:

```html
<div>
<section>
<article>
<p>
```

Characteristics:

- Takes full width by default
- Width, height, margin and padding works

---

## DevTools and the Box Model

Modern browsers provide developer tools to inspect the box model.

In browser DevTools you can see:

- Content size
- Padding
- Border
- Margin
- Computed dimensions

This helps debug spacing and layout issues quickly.

---

## Common Box Model Problems

### 1. Unexpected Overflow

Occurs when:

```css
width + padding + border > container width
```

Solution:

```css
box-sizing: border-box;
```

---

### 2. Extra Spacing Between Elements

Often caused by:

- Margin collapse
- Default browser margins
- Inline element whitespace

---

### 3. Layout Breaking on Small Screens

Large padding or fixed widths can cause responsive issues.

Solution:

- Use relative units
- Use `border-box`
- Use media queries

---

## Practical Example

### HTML

```html
<div class="card">
  <h2>Title</h2>
  <p>Content inside the card.</p>
</div>
```

### CSS

```css
.card {
  width: 300px;
  padding: 20px;
  border: 2px solid gray;
  margin: 30px auto;
  box-sizing: border-box;
}
```

### Result

- Card width stays exactly `300px`
- Content has internal spacing
- Border surrounds content
- Margin creates outer spacing
- Element is horizontally centered

---

## Best Practices

### Use `border-box` Globally

```css
* {
  box-sizing: border-box;
}
```

---

### Avoid Excessive Fixed Widths

Prefer:

```css
max-width
width: 100%
```

for responsive layouts.

---

### Use Consistent Spacing

Maintain consistent:

- `margin` values
- `padding` values
- layout spacing

---

### Inspect with DevTools

Always inspect elements visually during debugging.

---

## Inline versus Block Elements

HTML elements are mainly categorized into two types:

1. Block Elements
2. Inline Elements

Their behavior affects webpage layout, spacing, alignment, and styling.

---

## Block Elements

Block elements start on a new line and occupy the full available width of their parent container by default.

### Characteristics

- Start on a new line
- Take full available width
- Support `width` and `height`
- Support margin and padding on all sides
- Can contain inline and block elements

### Common Block Elements

```html
<div>
<p>
<section>
<article>
<header>
<footer>
<nav>
<ul>
<li>
```

### Example

```html
<div>First Block</div>
<div>Second Block</div>
<p>Paragraph</p>
```

### Output Behavior

```text
First Block

Second Block

Paragraph
```

### Styling Example

```css
div {
  width: 300px;
  padding: 20px;
  margin: 20px;
  background-color: lightblue;
}
```

---

## Inline Elements

Inline elements do not start on a new line. They only take up the width required by their content.

### Characteristics

- Stay on the same line
- Take only necessary width
- Usually ignore `width` and `height`
- Mainly used inside text content
- Support horizontal margin and padding

### Common Inline Elements

```html
<span>
<a>
<strong>
<em>
<b>
<i>
<label>
```

### Example

```html
<span>First Inline</span>
<span>Second Inline</span>
<a href="#">Link</a>
```

### Output Behavior

```text
First Inline Second Inline Link
```

### Styling Example

```css
span {
  background-color: yellow;
  padding: 10px;
}
```

---

## Key Differences

| Feature | Block Elements | Inline Elements |
|---|---|---|
| Starts on new line | Yes | No |
| Takes full width | Yes | No |
| Width and height work | Yes | Usually No |
| Vertical margin works | Yes | Limited |
| Flow direction | Vertical | Horizontal |

---

## Width Behavior

### Block Element

```html
<div class="box">Content</div>
```

```css
.box {
  background: lightblue;
}
```

The `<div>` stretches across the full width.

### Inline Element

```html
<span class="box">Content</span>
```

```css
.box {
  background: yellow;
}
```

The `<span>` only takes the width of its content.

---

## The `display` Property

CSS can change how elements behave.

### Convert Block to Inline

```css
div {
  display: inline;
}
```

### Convert Inline to Block

```css
span {
  display: block;
}
```

### Inline-Block

`inline-block` combines features of both inline and block elements.

```css
.box {
  display: inline-block;
  width: 150px;
  height: 100px;
}
```

Characteristics:

- Appears inline
- Supports width and height
- Supports full margin and padding

---

## Semantic Importance

Elements should be chosen based on meaning, not appearance.

Examples:

- `<p>` → paragraph content
- `<section>` → document section
- `<a>` → hyperlink
- `<span>` → inline text grouping

Using semantic elements improves:

- Accessibility
- SEO
- Readability
- Maintainability

---

## Common Mistakes

### Setting Width on Inline Elements

```css
span {
  width: 200px;
}
```

Usually does not work properly.

Solution:

```css
display: inline-block;
```

---

### Invalid Nesting

Incorrect:

```html
<span>
  <div></div>
</span>
```

Correct:

```html
<div>
  <span></span>
</div>
```

---

Block elements are used for larger structural sections of a webpage, while inline elements are used within text content. 

---
## Positioning: Relative and Absolute

CSS positioning controls how elements are placed on a webpage. Two commonly used positioning types are:

1. `position: relative`
2. `position: absolute`

These are essential for layouts, overlays, badges, dropdowns, tooltips, and many modern UI components.

---

### The `position` Property

The CSS `position` property defines how an element is positioned in the document.

Common values:

```css
static
relative
absolute
fixed
sticky
```

By default, all elements use:

```css
position: static;
```

---

### Relative Positioning

`position: relative` positions an element relative to its original position in the normal document flow.

The element still occupies its original space.

#### Syntax

```css
.box {
  position: relative;
}
```

---

### Offset Properties

Relative positioning works with:

```css
top
right
bottom
left
```

These move the element from its original location.

---

### Example

#### HTML

```html
<div class="box">Relative Box</div>
```

#### CSS

```css
.box {
  position: relative;
  top: 20px;
  left: 30px;
}
```

#### Result

The element moves:

- 20px downward
- 30px to the right

Its original space is still preserved.

---

### Important Characteristics of Relative Positioning

- Element remains in normal document flow
- Original space is maintained
- Used as a reference point for absolute elements
- Small positional adjustments become easy

---

### Common Uses of Relative Positioning

#### Minor Position Adjustments

```css
button {
  position: relative;
  top: 2px;
}
```

---

#### Parent Container for Absolute Elements

```css
.card {
  position: relative;
}
```

---

### Absolute Positioning

`position: absolute` removes the element from the normal document flow and positions it relative to the nearest positioned ancestor.

A positioned ancestor means a parent element with:

```css
position: relative;
position: absolute;
position: fixed;
position: sticky;
```

---

### Syntax

```css
.box {
  position: absolute;
}
```

---

### Example Without Positioned Parent

#### HTML

```html
<div class="box">Absolute Box</div>
```

#### CSS

```css
.box {
  position: absolute;
  top: 50px;
  left: 100px;
}
```

#### Result

The element is positioned relative to the webpage (`body`).

It no longer occupies normal layout space.

---

### Example With Positioned Parent

#### HTML

```html
<div class="container">
  <div class="box">Absolute Box</div>
</div>
```

#### CSS

```css
.container {
  position: relative;
  width: 400px;
  height: 200px;
  border: 2px solid black;
}

.box {
  position: absolute;
  top: 20px;
  right: 20px;
}
```

#### Result

The `.box` positions itself inside `.container`.

---

### Important Characteristics of Absolute Positioning

- Removed from normal document flow
- Other elements ignore its space
- Positioned relative to nearest positioned ancestor
- Supports precise placement

---

#3# Relative vs Absolute

| Feature | Relative | Absolute |
|---|---|---|
| Stays in normal flow | Yes | No |
| Original space preserved | Yes | No |
| Moves relative to | Original position | Positioned ancestor |
| Common use | Small adjustments | Exact placement |

---

### Real-World Example: Notification Badge

#### HTML

```html
<div class="icon">
  ICON
  <span class="badge">3</span>
</div>
```

#### CSS

```css
.icon {
  position: relative;
  font-size: 40px;
}

.badge {
  position: absolute;
  top: -10px;
  right: -10px;
}
```

#### Purpose

- `.icon` becomes positioning reference
- `.badge` is placed precisely on the corner

This pattern is widely used in:

- Notification badges
- Shopping cart counters
- Status indicators

---

### Stacking with `z-index`

Positioned elements can overlap.

`z-index` controls stacking order.

#### Example

```css
.box1 {
  position: absolute;
  z-index: 2;
}

.box2 {
  position: absolute;
  z-index: 1;
}
```

Higher `z-index` appears on top.

---

### Common Mistakes

#### Forgetting Positioned Parent

Incorrect:

```css
.child {
  position: absolute;
}
```

Without a positioned parent, the element positions relative to the page.

Correct:

```css
.parent {
  position: relative;
}
```

---

#### Using Absolute for Entire Layouts

Excessive absolute positioning can break responsive design.

Prefer:

- Flexbox
- Grid

for major layouts.

---

### Use Absolute for Small UI Components

Good use cases:

- Badges
- Tooltips
- Icons
- Overlays
- Dropdown menus

---

### Avoid Overusing Absolute Positioning

Too many absolutely positioned elements make layouts difficult to maintain.

---

Positioning adjusts elements while keeping them in the normal layout flow, whereas absolute positioning allows precise placement by removing elements from the flow and positioning them relative to a parent container.

---

## Common CSS Structural Classes

Structural classes are reusable CSS classes used to organize webpage layouts and UI structure.

These classes are commonly used in:

- Layout systems
- Cards
- Navigation bars
- Sections
- Containers
- Responsive designs

---

### Container Classes

Container classes control overall page width and alignment.

#### Example

```css
.container {
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
}
```

#### Purpose

- Centers content
- Prevents excessive stretching on large screens
- Maintains readable layouts

---

### Wrapper Classes

Wrappers group related elements together.

#### Example

```css
.wrapper {
  padding: 20px;
}
```

#### Usage

```html
<div class="wrapper">
  <section>Content</section>
</div>
```

Used for:

- Spacing
- Grouping sections
- Layout organization

---

### Row and Column Classes

Commonly used in grid systems.

#### Example

```css
.row {
  display: flex;
}

.column {
  flex: 1;
}
```

#### Usage

```html
<div class="row">
  <div class="column">One</div>
  <div class="column">Two</div>
</div>
```

#### Purpose

- Create horizontal layouts
- Build responsive grids
- Organize content sections

---

### Flex Utility Classes

Reusable classes for Flexbox layouts.

#### Center Alignment

```css
.flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

#### Space Between

```css
.flex-between {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

#### Column Layout

```css
.flex-column {
  display: flex;
  flex-direction: column;
}
```

---

### Grid Layout Classes

Used for CSS Grid layouts.

#### Example

```css
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
```

#### Usage

```html
<div class="grid">
  <div>Item</div>
  <div>Item</div>
  <div>Item</div>
</div>
```

---

### Card Classes

Cards are reusable UI containers.

#### Example

```css
.card {
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}
```

#### Usage

```html
<div class="card">
  <h2>Title</h2>
  <p>Content</p>
</div>
```

Common in:

- Dashboards
- Product listings
- Blog layouts

---

### Section Classes

Used to separate webpage content.

#### Example

```css
.section {
  padding: 60px 20px;
}
```

#### Purpose

- Maintain vertical spacing
- Improve readability
- Organize page structure

---

### Header and Footer Classes

#### Header

```css
.header {
  padding: 20px;
}
```

#### Footer

```css
.footer {
  padding: 30px;
  text-align: center;
}
```

These define major webpage regions.

---

### Navigation Classes

Used for menus and navigation bars.

#### Example

```css
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

#### Navigation Links

```css
.nav-links {
  display: flex;
  gap: 20px;
}
```

---

### Sidebar Classes

Used in dashboard or multi-column layouts.

#### Example

```css
.sidebar {
  width: 250px;
}
```

Often combined with Flexbox or Grid.

---

### Content Area Classes

Defines the main content region.

#### Example

```css
.main-content {
  flex: 1;
}
```

Usually paired with sidebars.

---

### Utility Spacing Classes

Reusable spacing helpers.

#### Margin Utilities

```css
.mt-20 {
  margin-top: 20px;
}

.mb-20 {
  margin-bottom: 20px;
}
```

#### Padding Utilities

```css
.p-20 {
  padding: 20px;
}
```

---

### Text Alignment Classes

#### Example

```css
.text-center {
  text-align: center;
}

.text-right {
  text-align: right;
}
```

Used frequently in reusable UI systems.

---

### Visibility Classes

Control element visibility.

### Hide Element

```css
.hidden {
  display: none;
}
```

#### Responsive Visibility

```css
.mobile-only {
  display: none;
}
```

Used with media queries.

---

### Responsive Structural Classes

Adapt layouts for different screen sizes.

### Example

```css
.responsive-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}
```

---

### Naming Conventions

Good structural class names should be:

- Clear
- Reusable
- Consistent

#### Good Examples

```css
.container
.card
.navbar
.sidebar
.section
```

#### Poor Examples

```css
.big-box
.red-area
```

Avoid styling-specific names when possible.

---

### BEM Naming Convention

A popular naming methodology.

#### Example

```css
.card
.card__title
.card__button
.card--featured
```

#### Structure

| Part | Meaning |
|---|---|
| Block | Main component |
| Element | Child component |
| Modifier | Variation |

---

### Example Page Structure

#### HTML

```html
<div class="container">
  
  <header class="header">
    Logo
  </header>

  <nav class="navbar">
    Navigation
  </nav>

  <section class="section">
    
    <div class="grid">
      <div class="card">Card 1</div>
      <div class="card">Card 2</div>
    </div>

  </section>

  <footer class="footer">
    Footer
  </footer>

</div>
```

---

### Benefits of Structural Classes

- Reusable code
- Cleaner HTML
- Easier maintenance
- Better scalability
- Consistent layouts
- Faster development

---

### Best Practices

### Keep Classes Reusable

Prefer:

```css
.card
```

instead of:

```css
.homepage-card
```

unless specificity is needed.

---

#### Avoid Deep Nesting

Prefer simpler structures for maintainability.

---

#### Separate Structure and Styling

Structural classes define layout, not visual themes.

---

#### Use Utility Classes Carefully

Too many utility classes can reduce readability.

---

CSS structural classes help organize webpage layouts efficiently. They provide reusable patterns for containers, grids, cards, navigation, spacing, and responsive design. Proper structural organization improves maintainability, consistency, scalability, and overall development workflow.

---

## Common CSS Styling Classes

### Text Styling

```css
.text-center {
  text-align: center;
}

.text-white {
  color: white;
}

.bold {
  font-weight: bold;
}
```

---

### Background Styling

```css
.bg-dark {
  background-color: #222;
}

.bg-light {
  background-color: #f5f5f5;
}
```

---

### Spacing Classes

```css
.mt-20 {
  margin-top: 20px;
}

.p-20 {
  padding: 20px;
}
```

---

### Border and Shadow

```css
.rounded {
  border-radius: 10px;
}

.shadow {
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}
```


---

### Button Styling

```css
.btn {
  padding: 10px 20px;
  border: none;
  cursor: pointer;
}

.btn-primary {
  background-color: blue;
  color: white;
}
```

---

### Width Utility

```css
.w-100 {
  width: 100%;
}
```

---

### Common Example

```html
<div class="bg-light p-20 rounded shadow">
  
  <h2 class="text-center">
    Welcome
  </h2>

  <button class="btn btn-primary">
    Submit
  </button>

</div>
```

---

## CSS Specificity

CSS specificity determines which CSS rule is applied when multiple rules target the same element.

The rule with higher specificity gets higher priority.

---

### Specificity Order

From lowest to highest priority:

```text
Element Selector < Class Selector < ID Selector < Inline CSS
```

---

### Element Selector

Lowest specificity.

```css
p {
  color: blue;
}
```

Targets all `<p>` elements.

---

### Class Selector

Higher priority than element selectors.

```css
.text-red {
  color: red;
}
```

```html
<p class="text-red">Hello</p>
```

---

### ID Selector

Higher priority than class selectors.

```css
#title {
  color: green;
}
```

```html
<h1 id="title">Heading</h1>
```

---

### Inline CSS

Highest normal specificity.

```html
<p style="color: orange;">
  Hello
</p>
```

---

### Example

```css
p {
  color: blue;
}

.text-red {
  color: red;
}

#heading {
  color: green;
}
```

```html
<p id="heading" class="text-red">
  Hello
</p>
```

### Result

```text
green
```

Reason:

- `ID` selector has highest specificity here.

---

### Specificity Values

| Selector | Value |
|---|---|
| Inline Style | 1000 |
| ID | 100 |
| Class / Attribute / Pseudo-class | 10 |
| Element / Pseudo-element | 1 |

---

### Comparison Example

```css
div p {
  color: blue;
}
```

Specificity:

```text
2
```

---

```css
.container p {
  color: red;
}
```

Specificity:

```text
11
```

`.container p` wins.

---

### `!important`

`!important` overrides normal specificity.

```css
p {
  color: red !important;
}
```

Avoid excessive usage because it makes CSS harder to maintain.

---

### Best Practices

- Prefer classes over IDs for styling
- Keep specificity low
- Avoid deep selector nesting
- Use `!important` sparingly

---

CSS specificity controls which styles are applied when conflicts occur.

---

## CSS Responsive Queries

CSS media queries are used to apply different styles for different screen sizes and devices.

They help create responsive websites.

---

### Basic Syntax

```css
@media (condition) {
  selector {
    property: value;
  }
}
```

---

### Common Breakpoints

| Device | Width |
|---|---|
| Mobile | `max-width: 767px` |
| Tablet | `768px - 1023px` |
| Desktop | `min-width: 1024px` |

---

### Mobile Query

```css
@media (max-width: 767px) {
  .container {
    flex-direction: column;
  }
}
```

Used for small screens.

---

### Tablet Query

```css
@media (min-width: 768px) and (max-width: 1023px) {
  .card {
    width: 50%;
  }
}
```

---

### Desktop Query

```css
@media (min-width: 1024px) {
  .card {
    width: 25%;
  }
}
```

---

### Responsive Layout Example

#### HTML

```html
<div class="container">
  <div class="box">One</div>
  <div class="box">Two</div>
</div>
```

#### CSS

```css
.container {
  display: flex;
  gap: 20px;
}

.box {
  flex: 1;
  padding: 20px;
  background: lightblue;
}
```

#### Responsive Query

```css
@media (max-width: 767px) {
  .container {
    flex-direction: column;
  }
}
```

Desktop:

```text
[ One ][ Two ]
```

Mobile:

```text
[ One ]
[ Two ]
```

---

### Mobile-First Approach

Write default styles for mobile first.

```css
.card {
  width: 100%;
}

@media (min-width: 768px) {
  .card {
    width: 50%;
  }
}
```

---

### Common Uses

- Responsive navigation
- Grid layouts
- Font resizing
- Hiding/showing elements
- Mobile layouts

---

### Best Practices

- Prefer mobile-first design
- Use relative units (`%`, `rem`, `vw`)
- Keep breakpoints consistent
- Test on multiple screen sizes

---

CSS media queries allow webpages to adapt to different devices and screen sizes, making responsive design possible.

---

## Flexbox and Grid

Flexbox and CSS Grid are modern CSS layout systems used for responsive webpage layouts.

- **Flexbox** → One-dimensional layouts
- **Grid** → Two-dimensional layouts

---

### Flexbox

Flexbox arranges items in rows or columns.

---

### Enable Flexbox

```css
.container {
  display: flex;
}
```

---

### Flex Container Properties

#### `flex-direction`

Defines main axis direction.

```css
flex-direction: row;
flex-direction: column;
```

Values:

```css
row
column
row-reverse
column-reverse
```

---

#### `justify-content`

Aligns items on the main axis.

```css
justify-content: center;
```

Values:

```css
flex-start
center
flex-end
space-between
space-around
space-evenly
```

---

#### `align-items`

Aligns items on the cross axis.

```css
align-items: center;
```

Values:

```css
stretch
center
flex-start
flex-end
baseline
```

---

#### `align-content`

Aligns multiple rows when wrapping exists.

Works only with:

```css
flex-wrap: wrap;
```

Example:

```css
align-content: center;
```

Values:

```css
stretch
center
flex-start
flex-end
space-between
space-around
space-evenly
```

---

#### `flex-wrap`

Controls wrapping.

```css
flex-wrap: wrap;
```

Values:

```css
nowrap
wrap
wrap-reverse
```

---

#### `flex-flow`

Shorthand for:

```css
flex-direction + flex-wrap
```

Example:

```css
flex-flow: row wrap;
```

---

#### `gap`

Spacing between flex items.

```css
gap: 20px;
```

---

### Flex Item Properties

#### `flex-grow`

Controls growing.

```css
flex-grow: 1;
```

---

#### `flex-shrink`

Controls shrinking.

```css
flex-shrink: 0;
```

---

#### `flex-basis`

Defines initial size.

```css
flex-basis: 200px;
```

---

#### `flex`

Shorthand property.

```css
flex: 1;
```

---

#### `align-self`

Overrides `align-items` for a single item.

```css
align-self: center;
```

---

#### `order`

Changes visual order.

```css
order: 2;
```

---

### Flexbox Example

```css
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 20px;
}
```

---

### Common Flexbox Uses

- Navbar
- Centering
- Menus
- Card rows
- Button groups

---

## CSS Grid

CSS Grid Layout is a two-dimensional layout system used to arrange content into rows and columns.

When `display: grid` is applied:

- The element becomes a **grid container**
- Its children become **grid items**

---

### Creating a Grid Container

```css
.container {
  display: grid;
}
```

---

### Defining Columns

```css
.container {
  grid-template-columns: 200px 200px 200px;
}
```

---

### Defining Rows

```css
.container {
  grid-template-rows: 100px 100px;
}
```

---

### Fraction Unit (`fr`)

```css
grid-template-columns: 1fr 2fr;
```

The second column gets twice the space.

---

### Repeat Notation

```css
grid-template-columns: repeat(3, 1fr);
```

Equivalent to:

```css
1fr 1fr 1fr
```

---

### Gap Between Tracks

```css
gap: 20px;
```

Also available:

```css
row-gap
column-gap
```

---

### Grid Lines

Grid lines divide rows and columns.

---

#### `grid-column-start`

```css
.item {
  grid-column-start: 1;
}
```

---

#### `grid-column-end`

```css
.item {
  grid-column-end: 3;
}
```

---

#### `grid-column`

Shorthand property.

```css
.item {
  grid-column: 1 / 3;
}
```

---

#### `grid-row-start`

```css
.item {
  grid-row-start: 1;
}
```

---

#### `grid-row-end`

```css
.item {
  grid-row-end: 3;
}
```

---

#### `grid-row`

Shorthand property.

```css
.item {
  grid-row: 1 / 3;
}
```

---

#### Spanning Tracks

```css
.item {
  grid-column: 1 / 4;
}
```

Spans across 3 columns.

---

### Grid Cells and Areas

#### Grid Cell

The space between four grid lines.

---

#### Grid Area

A rectangular area spanning one or more cells.

---

#### Auto Placement

Grid automatically places items into available cells.

```css
grid-auto-flow: row;
```

Values:

```css
row
column
dense
```

---

### Explicit and Implicit Grid

#### Explicit Grid

Defined manually using:

```css
grid-template-columns
grid-template-rows
```

---

#### Implicit Grid

Automatically created when extra items exist.

```css
grid-auto-rows: 100px;
```

---

### Alignment

#### `justify-items`

Aligns items horizontally inside cells.

```css
justify-items: center;
```

---

#### `align-items`

Aligns items vertically inside cells.

```css
align-items: center;
```

---

#### `place-items`

Shorthand for:

```css
justify-items + align-items
```

```css
place-items: center;
```

---

### Aligning the Entire Grid

#### `justify-content`

Aligns the grid horizontally.

```css
justify-content: center;
```

---

#### `align-content`

Aligns the grid vertically.

```css
align-content: center;
```

---

#### `place-content`

Shorthand for:

```css
justify-content + align-content
```

---

### Individual Item Alignment

#### `justify-self`

```css
justify-self: center;
```

---

#### `align-self`

```css
align-self: center;
```

---

#### `place-self`

Shorthand for:

```css
justify-self + align-self
```

---

### Example

#### HTML

```html
<div class="container">
  <div class="box">1</div>
  <div class="box">2</div>
  <div class="box">3</div>
</div>
```

#### CSS

```css
.container {
  display: grid;

  grid-template-columns:
    repeat(3, 1fr);

  gap: 20px;
}
```

---

#### Common Uses

- Dashboards
- Galleries
- Product grids
- Full-page layouts
- Responsive sections

---

CSS Grid is a powerful two-dimensional layout system that provides precise control over rows and columns.

---

## Common Header Meta Tags

Meta tags provide information about a webpage to browsers, search engines, and other web services. They are placed inside the `<head>` section of an HTML document.

---

#### Basic Structure

```html
<head>
  <meta charset="UTF-8">
</head>
```

---

### Character Encoding

Defines character encoding for the webpage.

```html
<meta charset="UTF-8">
```

`UTF-8` supports most languages and symbols.

---

### Viewport Meta Tag

Makes webpages responsive on mobile devices.

```html
<meta
  name="viewport"
  content="width=device-width, initial-scale=1.0"
>
```

---

### Page Description

Provides a short description for search engines.

```html
<meta
  name="description"
  content="Learn HTML and CSS basics."
>
```

---

### Keywords

Defines keywords related to the webpage.

```html
<meta
  name="keywords"
  content="HTML, CSS, Web Development"
>
```

---

### Author

Specifies the webpage author.

```html
<meta
  name="author"
  content="John Doe"
>
```

---

### Refresh or Redirect

Automatically refreshes or redirects the page.

```html
<meta
  http-equiv="refresh"
  content="5"
>
```

Redirect example:

```html
<meta
  http-equiv="refresh"
  content="5; url=https://example.com"
>
```

---

### Compatibility Mode

Improves compatibility with older browsers.

```html
<meta
  http-equiv="X-UA-Compatible"
  content="IE=edge"
>
```

---

### Open Graph Tags

Used when sharing webpages on social media.

#### Title

```html
<meta
  property="og:title"
  content="My Website"
>
```

#### Description

```html
<meta
  property="og:description"
  content="Learn web development."
>
```

#### Image

```html
<meta
  property="og:image"
  content="image.jpg"
>
```

---

### Theme Color

Sets browser theme color on mobile devices.

```html
<meta
  name="theme-color"
  content="#000000"
>
```

---

### Robots Meta Tag

Controls search engine crawling.

```html
<meta
  name="robots"
  content="index, follow"
>
```

Common values:

```text
index
noindex
follow
nofollow
```

---

### Favicon Link

Adds website icon.

```html
<link
  rel="icon"
  href="favicon.ico"
>
```

---

### CSS File Link

Links external CSS files.

```html
<link
  rel="stylesheet"
  href="styles.css"
>
```

---

### Example `<head>` Section

```html
<head>

  <meta charset="UTF-8">

  <meta
    name="viewport"
    content="width=device-width, initial-scale=1.0"
  >

  <meta
    name="description"
    content="HTML and CSS Tutorial"
  >

  <meta
    name="author"
    content="John Doe"
  >

  <title>My Website</title>

  <link
    rel="stylesheet"
    href="styles.css"
  >

</head>
```

---

## Best Practices

- Always use `UTF-8`
- Include viewport meta tag
- Add meaningful descriptions
- Keep meta descriptions concise
- Use Open Graph tags for social sharing

---

Meta tags provide essential information about webpages to browsers, search engines, and social media platforms. Proper use of meta tags improves SEO, responsiveness, accessibility, and sharing behavior.

---

# References

1. MDN Web Docs  
   https://developer.mozilla.org/

2. WHATWG HTML Standard  
   https://html.spec.whatwg.org/

3. W3C CSS Specifications  
   https://www.w3.org/Style/CSS/specs.en.html

4. CSS-Tricks  
   https://css-tricks.com/

5. W3Schools  
   https://www.w3schools.com/

6. web.dev — Learn CSS  
   https://web.dev/learn/css/
