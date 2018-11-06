# JavaScript


## nodejs

- [Helmet](https://github.com/helmetjs/helmet) (2018-09-18)

  Helmet helps you secure your Express apps by setting various HTTP headers.
  
- [React Helmet](https://github.com/nfl/react-helmet) (2018-09-18)

  This reusable React component will manage all of your changes to the document head.

- [Sequelize](https://github.com/sequelize/sequelize) (2018-09-20)

  Sequelize is a promise-based Node.js ORM for Postgres, MySQL, SQLite and Microsoft SQL Server.
  
- [pino](https://github.com/pinojs/pino) (2018-09-20)

  Very low overhead Node.js logger.
  
- [dotenv](https://github.com/motdotla/dotenv) (2018-09-20)

  Dotenv is a zero-dependency module that loads environment variables from a .env file into process.env.

- [DOMPurify](https://github.com/cure53/DOMPurify) (2018-09-18)

  DOMPurify is a DOM-only, super-fast, uber-tolerant XSS sanitizer for HTML, MathML and SVG.

- [Sanitizer](https://github.com/theSmaw/Caja-HTML-Sanitizer) (2018-09-18)

  Bundles Google Caja's HTML Sanitizer within a npm installable node.js module

- [Node License Finder](https://github.com/iandotkelly/nlf) (2018-09-18)

  Node License Finder is a utility for attempting to identify the licenses of modules in a node.js project. 
  
- [React Autosuggest](https://github.com/moroshko/react-autosuggest) (2018-10-12)

  WAI-ARIA compliant React autosuggest component
  
- [Istanbul Code Coverage](https://github.com/istanbuljs) (2018-10-17)

  Yet another JS code coverage tool that computes statement, line, function and branch coverage.
  - [Parsing Hints - Ignoring Lines](https://github.com/istanbuljs/nyc#parsing-hints-ignoring-lines)

## JavaScript

- [Title-Tag des inaktiven Browser-Tabs animieren](https://blog.kulturbanause.de/2018/01/title-tag-des-inaktiven-browser-tabs-animieren/) (2018-11-06)

```
focusTitle = $('head title').text(); // Originalen Title speichern
$(window).on('blur focus', function(e) {
 var prevType = $(this).data('prevType'); 
 if (prevType != e.type) {
   switch (e.type) {
     case 'blur':
     var i=0;
     tab = setInterval(function() {
       switch(i++%2) {
         case 0: document.title = 'Wir sind'; // Erste Anzeige im Tab
         break;
         case 1: document.title = 'kulturbanause'; // Zweite Anzeige im Tab
       }
     }, 1000); // Zeit zwischen dem Wechsel der Anzeigen
     break;
     case 'focus': 
       clearInterval(tab);
       document.title = focusTitle; // Originalen Title einsetzen
     break;
   }
 }
 $(this).data('prevType', e.type);
});
```

- [CSS Grid auto-fill – Responsive Layouts ohne Media Queries](https://blog.kulturbanause.de/2018/07/css-grid-auto-fill-responsive-layouts-ohne-media-queries/) (2018-11-06)

```
.container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
}
```


