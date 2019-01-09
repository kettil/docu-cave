# CSS Snippets


## Form hover

[Source](https://codepen.io/ericwbailey/pen/KQOpRM)
<details><summary>Show Code</summary><p>
  
```css
// Scale the form's size slightly when its input is focused.
// If `:focus-within` is not supported, form functionality is unaffected.
form:focus-within {
  box-shadow: 0px 0.2em 2.5em #c4c4c4;
  transform: scale(1.1); 
  
  // Remove the scaling for those who don't want animation.
  @media screen and (prefers-reduced-motion: reduce) {
    box-shadow: none;
    transform: none; 
  }
}
```
</p></details>
