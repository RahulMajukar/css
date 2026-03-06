Here's a well-structured Markdown file for your CSS Table Styling content, optimized for educational use:

```markdown
# CSS Table Styling Guide

CSS allows you to style HTML tables to make them more **readable**, **responsive**, and **visually appealing**. This guide covers borders, spacing, alignment, colors, hover effects, and responsive behavior.

## 1. Basic Table Structure

Start with a simple HTML table:

```html
<table>
  <tr>
    <th>Name</th>
    <th>Age</th>
    <th>City</th>
  </tr>
  <tr>
    <td>Rahul</td>
    <td>25</td>
    <td>Bangalore</td>
  </tr>
  <tr>
    <td>Anita</td>
    <td>23</td>
    <td>Mumbai</td>
  </tr>
</table>
```

## 2. Table Width

Control the overall table width:

```css
table {
  width: 100%; /* Full screen width */
  /* OR */
  /* width: 500px; */ /* Fixed width */
}
```

## 3. Table Borders

Define outlines for table and cells:

```css
table, th, td {
  border: 1px solid black;
}
```

**Border Properties:**
| Property     | Description          |
|--------------|----------------------|
| `border-width` | Thickness of border |
| `border-style` | Style of border     |
| `border-color` | Color of border     |

**Example:**
```css
table, th, td {
  border-width: 2px;
  border-style: solid;
  border-color: gray;
}
```

## 4. Border Collapse

Remove double borders between cells:

```css
table {
  border-collapse: collapse;
}
```

- **Without collapse**: Double borders appear
- **With collapse**: Single clean border

## 5. Table Padding

Add space inside table cells:

```css
th, td {
  padding: 10px;
}
```

**Visual Result:**
```
+-----------+
|   Rahul   |
+-----------+
```

## 6. Table Height

Control row heights:

```css
th {
  height: 70px;
}
td {
  height: 50px;
}
```

## 7. Text Alignment

Align content horizontally:

```css
th {
  text-align: left; /* left, center, right */
}
```

## 8. Vertical Alignment

Align content vertically:

```css
td {
  vertical-align: middle; /* top, middle, bottom */
}
```

## 9. Horizontal Row Lines

Add lines between rows for readability:

```css
th, td {
  border-bottom: 1px solid #ddd;
}
```

## 10. Table Hover Effect

Highlight rows on mouse hover:

```css
tr:hover {
  background-color: #f5f5f5;
}
```

## 11. Zebra Striped Tables

Alternating row colors:

```css
tr:nth-child(even) {
  background-color: #f2f2f2;
}
```

**Result:**
| Row | Color |
|-----|-------|
| 1   | White |
| 2   | Gray  |
| 3   | White |
| 4   | Gray  |

## 12. Table Header Styling

Make headers stand out:

```css
th {
  background-color: #04AA6D;
  color: white;
}
```

## 13. Responsive Tables

Enable horizontal scrolling on mobile:

**HTML:**
```html
<div class="tablecontainer">
  <table>
    <!-- table content -->
  </table>
</div>
```

**CSS:**
```css
.tablecontainer {
  overflow-x: auto;
}
```

## 14. Complete Example

**Full CSS:**
```css
table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  padding: 12px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}

th {
  background-color: #4CAF50;
  color: white;
}

tr:hover {
  background-color: #f5f5f5;
}

tr:nth-child(even) {
  background-color: #f2f2f2;
}

.tablecontainer {
  overflow-x: auto;
}
```

**Complete HTML:**
```html
<div class="tablecontainer">
  <table>
    <tr>
      <th>Name</th>
      <th>Age</th>
      <th>City</th>
    </tr>
    <tr>
      <td>Rahul</td>
      <td>25</td>
      <td>Bangalore</td>
    </tr>
    <tr>
      <td>Anita</td>
      <td>23</td>
      <td>Mumbai</td>
    </tr>
  </table>
</div>
```

## ✅ Features Included

This complete table styling provides:
- ✅ Clean borders with `border-collapse`
- ✅ Proper padding and spacing
- ✅ Colored header background
- ✅ Row hover effects
- ✅ Zebra striped rows
- ✅ Responsive horizontal scrolling

---

**Perfect for your CSS teaching content, Rahul!** This MD file is ready for GitHub, YouTube descriptions, or your educational platform.

Would you like me to add a live CodePen demo link or create a React component version of this table?
