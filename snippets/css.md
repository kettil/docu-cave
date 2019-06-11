# CSS Snippets

## Form hover

[Source](https://codepen.io/ericwbailey/pen/KQOpRM) (2019-01-09)

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

## Responsive layouts without media queries

[Source](https://blog.kulturbanause.de/2018/07/css-grid-auto-fill-responsive-layouts-ohne-media-queries/) (2018-11-06)

<details><summary>Show Code</summary><p>

```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
}
```

</p></details>

## Meter-Element - star rating (like Amazon)

[Source](https://codepen.io/maddesigns/pen/oQoMre) (2019-01-09)

<details><summary>Show Code</summary><p>

```html
<meter value="70" min="0" max="100" low="20" high="80" optimum="90"
50% satisfied costumers – 2.5 of 5.0 stars</meter
>
```

```css
$meter-background: url('data:image/svg+xml,%3Csvg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"%3E%3Ctext font-size="100" y="0.9em" stroke-linejoin="round" fill="white" stroke="darkorange" stroke-width="4"%3E★%3C/text%3E%3C/svg%3E')
  0 / auto 100%;
$meterbar: url('data:image/svg+xml,%3Csvg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"%3E%3Ctext font-size="100" y="0.9em" stroke-linejoin="round" fill="gold" stroke="darkorange" stroke-width="4"%3E★%3C/text%3E%3C/svg%3E')
  0 / auto 100%;

meter {
  $meter-height: 4em;

  background: $meter-background;
  height: $meter-height;
  width: $meter-height * 5;
}

meter::-webkit-meter-bar {
  background: $meter-background;
}

/* firefox styling for the bar (filled stars) */
meter:-moz-meter-optimum::-moz-meter-bar,
meter:-moz-meter-sub-optimum::-moz-meter-bar,
meter:-moz-meter-sub-sub-optimum::-moz-meter-bar {
  background: $meterbar;
}

/* webkit styling for the bar (filled stars) */
meter::-webkit-meter-optimum-value,
meter::-webkit-meter-suboptimum-value,
meter::-webkit-meter-even-less-good-value {
  background: $meterbar;
}

// defaults
* {
  box-sizing: border-box;
}

html {
  height: 100%;
}

body {
  display: flex;
  height: 100vh;
  align-items: center;
  justify-content: center;
}
```

</p></details>
