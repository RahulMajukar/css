```markdown
# CSS Grid Layout Guide

CSS Grid creates powerful **2D layouts** with rows and columns for complex web designs. It's perfect for responsive page layouts, dashboards, galleries, and modern websites.

**Visual Example:**
```
| Header  Header  Header |
| Sidebar Content  Ads   |
| Footer  Footer  Footer |
```

## 1. Enable Grid Layout

Set container to `display: grid`:

**CSS:**
```css
.container {
  display: grid;
}
```

**HTML:**
```html
<div class="container">
  <div>Box 1</div>
  <div>Box 2</div>
  <div>Box 3</div>
</div>
```

## 2. Grid Columns

Define column structure with `grid-template-columns`:

**Fixed Width:**
```css
.container {
  display: grid;
  grid-template-columns: 200px 200px 200px;
}
```

**Fractional Units (fr):**
```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}
```

**Output:**
```
| Box1 | Box2 | Box3 |
```
*Each column = equal fraction of available space*

## 3. Grid Rows

Set row heights:

```css
.container {
  display: grid;
  grid-template-rows: 100px 100px;
}
```

**Output:**
```
| Box1 | Box2 |
| Box3 | Box4 |
```

## 4. Grid Gap

Add spacing between items:

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 20px; /* row-gap + column-gap */
}
```

**Gap Properties:**
| Property    | Description             |
|-------------|-------------------------|
| `gap`       | Both rows & columns     |
| `row-gap`   | Space between rows      |
| `column-gap`| Space between columns   |

## 5. Grid Item Placement

Control item positioning:

**Span Columns:**
```css
.item1 {
  grid-column: 1 / 3; /* Starts at column 1, ends before column 3 */
}
```

**Output:**
```
| Box1 spans 2 columns |
| Box2 | Box3         |
```

**Span Rows:**
```css
.item2 {
  grid-row: 1 / 3;
}
```

## 6. Grid Template Areas

Name areas for intuitive layouts:

**CSS:**
```css
.container {
  display: grid;
  grid-template-areas:
    "header header header"
    "sidebar content ads"
    "footer footer footer";
  gap: 20px;
  grid-template-columns: 200px 1fr 150px;
  grid-template-rows: 80px 1fr 60px;
}
```

**HTML:**
```html
<div class="container">
  <div class="header">Header</div>
  <div class="sidebar">Sidebar</div>
  <div class="content">Content</div>
  <div class="ads">Ads</div>
  <div class="footer">Footer</div>
</div>
```

**Assign Areas:**
```css
.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.content { grid-area: content; }
.ads { grid-area: ads; }
.footer { grid-area: footer; }
```

**Perfect Layout:**
```
| Header  Header  Header |
| Sidebar Content  Ads   |
| Footer  Footer  Footer |
```

## 7. Align Grid Items

Control content alignment:

**Horizontal:**
```css
justify-items: center; /* start, end, center, stretch */
```

**Vertical:**
```css
align-items: center; /* start, end, center, stretch */
```

**Complete Example:**
```css
.container {
  display: grid;
  justify-items: center;
  align-items: center;
}
```

## 8. Responsive Grid

Auto-adjust columns for any screen:

```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
}
```

**Magic:** 
- Min column width = 200px
- Auto-adjusts number of columns
- Perfect for card galleries!

## 9. Complete Practical Example

**HTML:**
```html
<div class="container">
  <div class="box">1</div>
  <div class="box">2</div>
  <div class="box">3</div>
  <div class="box">4</div>
  <div class="box">5</div>
  <div class="box">6</div>
</div>
```

**CSS:**
```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  padding: 20px;
}

.box {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 30px;
  text-align: center;
  font-size: 24px;
  font-weight: bold;
  border-radius: 12px;
  box-shadow: 0 8px 32px rgba(0,0,0,0.1);
}
```

**Output:**
```
|  1  |  2  |  3  |
|  4  |  5  |  6  |
```

## 10. Grid vs Flexbox

| Feature          | CSS Grid              | Flexbox             |
|------------------|-----------------------|---------------------|
| **Layout Type**  | 2D (rows + columns)   | 1D (row OR column)  |
| **Complex Layouts** | ✅ Excellent        | ⚠️ Limited         |
| **Page Layouts** | ✅ Perfect            | ❌ Not ideal        |
| **Components**   | ⚠️ Overkill           | ✅ Perfect          |

## 🎯 When to Use CSS Grid

**Perfect for:**
- 📱 **Website layouts** (header/sidebar/content/footer)
- 📊 **Dashboards & admin panels**
- 🖼️ **Image galleries & card grids**
- 🛒 **Product catalogs**
- 💼 **Portfolio websites**

## ✅ Key Takeaways

This guide covers:
- ✅ Basic grid setup
- ✅ Column/row definitions
- ✅ Template areas for layouts
- ✅ Responsive auto-fit
- ✅ Real-world examples
- ✅ Grid vs Flexbox comparison

---

**Ready for your CSS Grid teaching module, Rahul!** This content works great with your Table & List styling guides.

**Next?** Want 5 real-world CSS Grid layouts (Dashboard, Gallery, Blog, Landing Page, E-commerce) with live CodePen demos?
```

This MD file is optimized for your teaching workflow with:
- ✅ Syntax-highlighted code blocks
- ✅ Visual layout diagrams
- ✅ Comparison tables
- ✅ Practical complete examples
- ✅ Responsive techniques
- ✅ Modern styling with gradients/shadows

Perfect companion to your Table Styling and List Styling content! 🚀


``` html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .container {
            display: grid;
            /* grid-template-columns: 200px 200px 200px; */
            /* grid-template-columns: 1fr 1fr 1fr; */
            /* grid-template-columns: repeat(3, 1fr); */
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            row-gap: 120px;
            column-gap: 120px;
            gap: 120px;
            grid-template-rows: 100px 100px;
            
        }

        .box {
            background-color: lightgray;
            border: 1px solid #ccc;
            padding: 10px;
            text-align: center;
        }

        .item2 {
            background-color: lightblue;

            /* grid-column-start: 1;
            grid-column-end: 3; */
            /* grid-column: 1 / 3; */

            /* grid-row-start: 1;
            grid-row-end: 3; */
            /* grid-row: 1 / 3; */

            /* grid-area: 1 / 1 / 3 / 3; */
             /* grid-area: 1 / 1 / 3 / 3; */

        }
    </style>
</head>

<body>
    <div class="container">
        <div class="box item1">Box 1</div>
        <div class="box item2">Box 2</div>
        <div class="box item3">Box 3</div>
        <div class="box item3">Box 3</div>
        <div class="box item3">Box 3</div>
    </div>
</body>

</html>
```
