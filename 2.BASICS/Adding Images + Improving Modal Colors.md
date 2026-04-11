# 📱 React Native — Adding Images + Improving Modal Colors (GoalInput Modal)

## 🎯 Goal

Improve the app UI by:

- Adding an image above the TextInput (inside the modal)
    
- Adjusting colors so the image/background fits
    
- Understanding how images work in React Native (different from web)
    

---

# 🖼️ 1) The Image component in React Native

React Native has a built-in component:

```
Image
```

You import it from `react-native` and use it in JSX like other components.

Example placement here:

- Inside `GoalInput`
    
- Above the `TextInput`
    

---

# 📁 2) Where to store images (project structure)

Static assets like images should go in:

```
assets/
  images/
    goal.png
```

So you create an `images` folder inside `assets`, and place the provided image there.

---

# 🔗 3) Important: Image source works differently than the web

On the web, you might do:

```
src="assets/images/goal.png"
```

That **does NOT work** in React Native for local images.

✅ For local images, you use:

```
require("relative-path")
```

And the path must be **relative to the file where you’re using it**.

Since `GoalInput.js` is in `components/`, you go up one folder first:

```
../assets/images/goal.png
```

Example:

```
<Image source={require("../assets/images/goal.png")} />
```

---

# 🎨 4) Styling the image

React Native `Image` supports `style`.

You typically set at least:

- width
    
- height
    

Example style object:

```
image: {
  width: 100,
  height: 100,
  margin: 20
}
```

And apply:

```
<Image
  style={styles.image}
  source={require("../assets/images/goal.png")}
/>
```

---

# ⚠️ Why the image might “not appear”

If the image is white and your background is white, it’s there but invisible.

So the fix is not the image—it’s the background.

---

# 🎨 5) Styling the Modal background correctly

Even though `Modal` has props, the common pattern to style the background is:

✅ Style the **root View inside the Modal**, not the Modal itself.

So on your `inputContainer` (the root View inside the modal), add:

- `backgroundColor: "#311b6b"` (dark purple)
    

Example:

```
inputContainer: {
  flex: 1,
  justifyContent: "center",
  padding: 16,
  backgroundColor: "#311b6b"
}
```

Now the image becomes visible.

---

# 🧹 6) Clean up old styles that no longer make sense

Because layout changed and you’re using a modal now:

- Remove bottom border (looks weird now)
    
- Remove unnecessary marginBottom
    

This keeps styles consistent with the new UI.

---

# ✅ What’s achieved in this step

✅ Image added above input inside the modal  
✅ Local image loaded using `require()`  
✅ Modal background updated so the image is visible  
✅ Old styles removed (border/margin that no longer fit)

---

# 🔜 What’s next (as mentioned)

Now that the modal has a dark background:

- TextInput text color may need adjustment (so typed text is visible)
    
- Buttons look out of place (default button styling doesn’t match)
    

Next step is improving styling for:

- TextInput appearance (text color, background, etc.)
    
- Buttons color consistency (or build custom buttons with Pressable)