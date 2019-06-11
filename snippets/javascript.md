# Git

## Title-Tag des inaktiven Browser-Tabs animieren

[Source](https://blog.kulturbanause.de/2018/01/title-tag-des-inaktiven-browser-tabs-animieren/) (2018-11-06)

<details><summary>Show Code</summary><p>

```javascript
focusTitle = $("head title").text(); // Originalen Title speichern
$(window).on("blur focus", function(e) {
  var prevType = $(this).data("prevType");
  if (prevType != e.type) {
    switch (e.type) {
      case "blur":
        var i = 0;
        tab = setInterval(function() {
          switch (i++ % 2) {
            case 0:
              document.title = "Wir sind"; // Erste Anzeige im Tab
              break;
            case 1:
              document.title = "kulturbanause"; // Zweite Anzeige im Tab
              break;
          }
        }, 1000); // Zeit zwischen dem Wechsel der Anzeigen
        break;
      case "focus":
        clearInterval(tab);
        document.title = focusTitle; // Originalen Title einsetzen
        break;
    }
  }
  $(this).data("prevType", e.type);
});
```

</p></details>
