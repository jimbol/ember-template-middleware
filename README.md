ember-template-middleware takes the functionallity of toranb's [ember-template-compiler](https://github.com/toranb/ember-template-compiler)
and makes configurable middleware out of it.

##Features
- Render ember templates in node js as middleware
- Outputs AMD and `Ember.TEMPLATE` objects

##Requires
- [mkdirp](https://github.com/substack/node-mkdirp)
- [ember-template-compiler](https://github.com/toranb/ember-template-compiler)

##What can I do with this?

To activate middleware require ember-template-compiler and then configure.

	var compiler = require('ember-template-compiler');

A simple setup will look something like: 

	app.use(compiler.middleware({
		src: 	 	__dirname + '/handlebars',
		dest: 	 	__dirname,
		format:		'AMD'
	}));


- `src`: Hbs file folder. Do not include `__dirname` if origin not defined, **REQUIRED**
- `dest`: Output destination. Do not include `__dirname` if origin not defined, **REQUIRED**
- `origin`: Origin directory, **DEFAULT: false**
- `force`: Force compile, **DEFAULT: false**
- `format`: Output format. Either `'AMD'` or `null`.  `null` outputs an `Ember.TEMPLATES` property
- `namePrefix`: Prefix for template name 
- `pathInName`: Include path in name, **DEFAULT: true**

If the `origin` is defined. `src` and `dest` will be relative to it.  

	app.use(compiler.middleware({
		src: 	 	'/js/app/handlebars',
		dest: 	 	'/js/app/templates',
		origin:  	'/var/www/frontend/public',
		namePrefix: 'app/templates',
		format:  	'AMD',
		force: 		true
	}));

## License

Copyright © 2013 Jim Hall

Licensed under the MIT License
