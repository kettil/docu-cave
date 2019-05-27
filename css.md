# CSS

## Grid

- [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) (2018-11-15)

  > Flexbox Guide
  
- [CSS Grid – Einführung in Gestaltungsraster mit dem Grid Layout Module](https://blog.kulturbanause.de/2013/12/css-grid-layout-module/) (2018-11-15)

  > Komplexe Weblayouts lassen sich weder mit float-basierten Gestaltungsrastern noch mit Flexbox perfekt umsetzen. 

- [CSS Grid auto-fill – Responsive Layouts ohne Media Queries](https://blog.kulturbanause.de/2018/07/css-grid-auto-fill-responsive-layouts-ohne-media-queries/) (2018-11-06)

  > <details><summary>Show Code</summary><p>
  >   
  > ```css
  > .container {
  >     display: grid;
  >     grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  > }
  > ```
  > 
  > </p></details>
  
- [Native CSS Grid Layouts ohne Framework – ein einfaches Beispiel](http://maddesigns.de/css-grid-layout-2764.html) (2018-11-21)

  > Eine neue CSS Grid Layout Spezifikation gibt Webworkern nun die Möglichkeit eigene Grids nach den jeweiligen Anforderungen selbst zu definieren. Das ist nicht nur für Seitenlayouts, sondern auch für Modul-Layouts sehr nützlich. Aber zugegeben sind auch sehr viele neue Eigenschaften zu lernen, 17 neue Eigenschaften in Summe.

- [CSS Grid Application Layout in Production](https://techblog.commercetools.com/gss-grid-application-layout-in-production-f60c65a05cfa) (2018-12-04)

  > CSS Grid is one of the biggest enhancements for layouts the web has seen in a long time.
  > We are finally able to create native two-dimensional layouts in the browser.
  > It makes your HTML more concise and your CSS more robust.

- [Learning CSS Grid](https://varun.ca/css-grid/) (2019-01-02)

  > The learning curve was much steeper than I expected – the module introduces something like 17 new concepts.

## FlexBox  
  
- [CSS Flexbox – Einführung in das Flexible Box Layout Module](https://blog.kulturbanause.de/2013/07/einfuhrung-in-das-flexbox-modell-von-css/) (2018-11-15)

  > Das sog. »CSS Flexible Box Layout Module« – kurz Flexbox – stellt neben CSS Grid eine der beiden wesentlichen Techniken zur Gestaltung von Layouts mit CSS dar.
  
- [Flexbox: Mehrspaltige Liste von Boxen mit vertikal zentrierten Inhalten](https://blog.kulturbanause.de/2016/03/flexbox-mehrspaltige-liste-von-boxen-mit-vertikal-zentrierten-inhalten/) (2018-11-15)

  > Vertikales Zentrieren einerseits und gleich hohe Elemente andererseits stellten Webdesigner lange Zeit vor große Herausforderungen. Dank Flexbox gehört dies mittlerweile der Vergangenheit an.
  
  
## Images

- [object-fit](https://css-tricks.com/almanac/properties/o/object-fit/) (2019-01-02)

  > The object-fit property defines how an element responds to the height and width of its content box. 
  
- [Essential Guide for Web Performance Optimization](https://uxplanet.org/essential-guide-for-web-performance-optimization-1b883d638a1) (2019-0275)

  > Article about web performance (see [Responsive Image Breakpoints Generator](https://www.responsivebreakpoints.com))
  
## React

- [JSS](https://cssinjs.org/react-jss/?v=v10.0.0-alpha.16) ([npm](https://www.npmjs.com/package/react-jss) | [github](https://github.com/cssinjs/jss/tree/master/packages/react-jss)) (2019-04-13)

  > JSS is an authoring tool for CSS which allows you to use JavaScript to describe styles in a declarative, conflict-free and reusable way. It can compile in the browser, server-side or at build time in Node.
  
## Meter-Element

- [star rating (like Amazon)](https://codepen.io/maddesigns/pen/oQoMre) (2019-01-09)

  > <details><summary>Show Code</summary><p>
  >   
  > ```html
  > <meter value="70" min="0" max="100" low="20" high="80" optimum="90">50% satisfied costumers – 2.5 of 5.0 stars</meter>
  > ```
  >
  > ```css
  > $meter-background: url('data:image/svg+xml,%3Csvg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"%3E%3Ctext font-size="100" y="0.9em" stroke-linejoin="round" fill="white" stroke="darkorange" stroke-width="4"%3E★%3C/text%3E%3C/svg%3E')
  > 		0 / auto 100%;
  > $meterbar: url('data:image/svg+xml,%3Csvg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"%3E%3Ctext font-size="100" y="0.9em" stroke-linejoin="round" fill="gold" stroke="darkorange" stroke-width="4"%3E★%3C/text%3E%3C/svg%3E')
  > 		0 / auto 100%;
  > 
  > meter {
  > 	$meter-height: 4em;
  > 	
  > 	background: $meter-background;
  > 	height: $meter-height;
  > 	width: $meter-height * 5;
  > }
  > 	
  > meter::-webkit-meter-bar {
  > 	background: $meter-background;
  > }
  > 
  > /* firefox styling for the bar (filled stars) */
  > meter:-moz-meter-optimum::-moz-meter-bar,
  > meter:-moz-meter-sub-optimum::-moz-meter-bar,
  > meter:-moz-meter-sub-sub-optimum::-moz-meter-bar {
  > 	background: $meterbar;
  > }
  > 
  > /* webkit styling for the bar (filled stars) */
  > meter::-webkit-meter-optimum-value,
  > meter::-webkit-meter-suboptimum-value,
  > meter::-webkit-meter-even-less-good-value {
  > 	background: $meterbar;
  > }
  > 
  > // defaults
  > * {
  > 	box-sizing: border-box;
  > }
  > 
  > html {
  > 	height: 100%;
  > }
  > 	
  > body {
  > 	display: flex;
  > 	height: 100vh;
  > 	align-items: center;
  > 	justify-content: center;
  > }
  > ```
  > 
  > </p></details>
