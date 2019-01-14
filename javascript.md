# JavaScript


## General

- [JavaScript-Equality-Table](https://dorey.github.io/JavaScript-Equality-Table/) (2018-11-29)

## nodejs

- [Helmet](https://github.com/helmetjs/helmet) (2018-09-18)

  > Helmet helps you secure your Express apps by setting various HTTP headers.
  
- [React Helmet](https://github.com/nfl/react-helmet) (2018-09-18)

  > This reusable React component will manage all of your changes to the document head.

- [Sequelize](https://github.com/sequelize/sequelize) (2018-09-20)

  > Sequelize is a promise-based Node.js ORM for Postgres, MySQL, SQLite and Microsoft SQL Server.
  
- [debug](https://github.com/visionmedia/debug) (2018-12-26)

  > A tiny JavaScript debugging utility modelled after Node.js core's debugging technique.
  
- [pino](https://github.com/pinojs/pino) (2018-09-20)

  > Very low overhead Node.js logger.
  
- [dotenv](https://github.com/motdotla/dotenv) (2018-09-20)

  > Dotenv is a zero-dependency module that loads environment variables from a .env file into process.env.

- [DOMPurify](https://github.com/cure53/DOMPurify) (2018-09-18)

  > DOMPurify is a DOM-only, super-fast, uber-tolerant XSS sanitizer for HTML, MathML and SVG.

- [Sanitizer](https://github.com/theSmaw/Caja-HTML-Sanitizer) (2018-09-18)

  > Bundles Google Caja's HTML Sanitizer within a npm installable node.js module

- [Node License Finder](https://github.com/iandotkelly/nlf) (2018-09-18)

  > Node License Finder is a utility for attempting to identify the licenses of modules in a node.js project. 
  
- [React Autosuggest](https://github.com/moroshko/react-autosuggest) (2018-10-12)

  > WAI-ARIA compliant React autosuggest component
  
- [Istanbul Code Coverage](https://github.com/istanbuljs) (2018-10-17)

  > Yet another JS code coverage tool that computes statement, line, function and branch coverage.
  > - [Parsing Hints - Ignoring Lines](https://github.com/istanbuljs/nyc#parsing-hints-ignoring-lines)

- [restify](http://restify.com) (2018-12-04)

  > restify is a framework, utilizing connect style middleware for building REST APIs.
  
- [Learn RxJS](https://www.learnrxjs.io) (2018-12-13)

  > RxJS is one of the hottest libraries in web development today. Offering a powerful, functional approach for dealing with events and with integration points into a growing number of frameworks, libraries, and utilities, the case for learning Rx has never been more appealing.
  
- [RxJS examples](https://xgrommx.github.io/rx-book/content/observable/observable_instance_methods/index.html) (2018-12-13)

  Interactive examples of RxJS - **warning old code version (v4)**
  
- [Faker.js](https://github.com/Marak/Faker.js) (2018-12-14)

  > faker.js - generate massive amounts of fake data in the browser and node.js
  
- [as-table](https://github.com/xpl/as-table) (2019-01-02) 

  > A simple function that prints objects as ASCII tables. 
  > Supports ANSI styling and weird Unicode 💩 emojis – they won't break the layout.
  
- [Yargs](https://github.com/yargs/yargs) (2019-01-02)

  > Yargs be a node.js library fer hearties tryin' ter parse optstrings
  
- [meow](https://github.com/sindresorhus/meow) (2019-01-02)

  > CLI app helper (Parses arguments)

- [Chalk](https://github.com/chalk/chalk) (2019-01-02)  

  > Terminal string styling done right

- [Prompt](https://github.com/flatiron/prompt) (2019-01-02)

  > A beautiful command-line prompt for node.js
  
- [ora](https://github.com/sindresorhus/ora) (2019-01-02)
  
  > Elegant terminal spinner

- [Joi](https://github.com/hapijs/joi) (2019-01-14)

  > Object schema description language and validator for JavaScript objects.

- [jsonschema](https://github.com/tdegrunt/jsonschema) (2019-01-14)

  > JSON schema validator, which is designed to be fast and simple to use.
  
- [Parcel](https://github.com/parcel-bundler/parcel) (2019-01-14)

  > Blazing fast, zero configuration web application bundler
  
- [node.bcrypt.js](https://github.com/kelektiv/node.bcrypt.js) (2019-01-14)

  > bcrypt for NodeJs

## JavaScript

- [Title-Tag des inaktiven Browser-Tabs animieren](https://blog.kulturbanause.de/2018/01/title-tag-des-inaktiven-browser-tabs-animieren/) (2018-11-06)

> <details><summary>Show Code</summary><p>
>   
> ```javascript
> focusTitle = $('head title').text(); // Originalen Title speichern
> $(window).on('blur focus', function(e) {
>  var prevType = $(this).data('prevType'); 
>  if (prevType != e.type) {
>    switch (e.type) {
>      case 'blur':
>      var i=0;
>      tab = setInterval(function() {
>        switch(i++%2) {
>          case 0: document.title = 'Wir sind'; // Erste Anzeige im Tab
>          break;
>          case 1: document.title = 'kulturbanause'; // Zweite Anzeige im Tab
>        }
>      }, 1000); // Zeit zwischen dem Wechsel der Anzeigen
>      break;
>      case 'focus': 
>        clearInterval(tab);
>        document.title = focusTitle; // Originalen Title einsetzen
>      break;
>    }
>  }
>  $(this).data('prevType', e.type);
> });
> ```
> 
> </p></details>
