---
title: Positioning
weight: 6
--- 


> Positioning in CSS determines how elements are placed on the webpage relative to their parent, other elements, or the viewport. The `position` property is the key to this behavior and can take the following values:

---

# **`static` (Default Position)**
- **Behavior:**  
  The element follows the normal document flow. This is the default behavior of all elements.  
- **Characteristics:**  
  - No special positioning.  
  - Offsets (`top`, `right`, `bottom`, `left`) **do not apply**.

**Example:**
```css
div {
  position: static; /* Default */
}
```

---

### 2. **`relative`**
- **Behavior:**  
  The element is positioned relative to its normal position in the flow.  
- **Characteristics:**  
  - Offsets (`top`, `right`, `bottom`, `left`) shift the element without affecting others.  
  - The space originally occupied by the element remains reserved.

**Example:**
```css
div {
  position: relative;
  top: 10px; /* Moves 10px down */
  left: 20px; /* Moves 20px to the right */
}
```

---

### 3. **`absolute`**
- **Behavior:**  
  The element is removed from the normal flow and positioned relative to the **nearest positioned ancestor** (an ancestor with `position` set to `relative`, `absolute`, or `sticky`). If no such ancestor exists, it is positioned relative to the `<html>` (viewport).  
- **Characteristics:**  
  - Offsets (`top`, `right`, `bottom`, `left`) determine the position.  
  - Other elements do not recognize the space it would have occupied.

**Example:**
```css
div {
  position: absolute;
  top: 50px;
  left: 100px;
}
```

---

### 4. **`fixed`**
- **Behavior:**  
  The element is removed from the flow and positioned relative to the **viewport**. It does not move when the page is scrolled.  
- **Characteristics:**  
  - Useful for sticky headers or floating buttons.  
  - Offsets (`top`, `right`, `bottom`, `left`) apply relative to the viewport.

**Example:**
```css
div {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%; /* Full width of the viewport */
}
```

---

### 5. **`sticky`**
- **Behavior:**  
  The element behaves as `relative` until a specific scroll position is reached, after which it behaves as `fixed`.  
- **Characteristics:**  
  - Requires at least one offset (`top`, `right`, `bottom`, `left`).  
  - Sticks to its scroll container until the boundary is reached.

**Example:**
```css
div {
  position: sticky;
  top: 10px; /* Sticks 10px below the top of its container */
}
```

---

### 6. **Offsets and Usage**
Offsets (`top`, `right`, `bottom`, `left`) specify how far the element should move.  
- For `relative`, they adjust the position **relative to its normal flow**.  
- For `absolute`, `fixed`, and `sticky`, they adjust the position **relative to the containing block or viewport**.

---

### Visual Summary

| **Position Value** | **Relative To**                      | **Offset Properties Work?** | **Affects Layout?** |
|---------------------|--------------------------------------|------------------------------|----------------------|
| `static`            | Default flow                       | No                           | Yes                  |
| `relative`          | Default position in the flow        | Yes                          | Yes (original space is reserved) |
| `absolute`          | Nearest positioned ancestor or `<html>` | Yes                          | No                   |
| `fixed`             | Viewport                           | Yes                          | No                   |
| `sticky`            | Scroll position + container bounds | Yes                          | Yes (original space is reserved) |

---
