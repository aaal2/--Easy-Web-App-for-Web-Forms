# Easy Web App
Create web applications easily. 

This is a Node.js API for the [rest-web-gui](https://github.com/ma-ha/rest-web-ui) framework.

Focus is on _web applications_ (not simple web pages). A lot of "make-it-simple" plug-ins are available:
* forms
* tables / lists
* content
* I/O: control switches/drawer, gauges, graphs, LEDs, displays, ...
* i18n: switch language
* maps: POIs, routes, traffic, ...
* page to page navigation with navigation tabs, menus, links and session data
* source code display
* basic OAuth security
* ...

Check out [docu on "rest-web-gui" GIT project](https://github.com/ma-ha/rest-web-ui/) 
and [online demos](http://mh-svr.de/pong_dev) of features.

## Compared with ...
* jade
  * jade is descriptive, but low level (HTML structure)
  * jade is perfect for web pages, not for web applications
* angular 
  * angular can do everything, but JS programming is required

## Node.js example
This creates a web page with a form view to add customers and a result view:

```javascript
// initialize:
var gui = require ( 'easy-web-app' )

gui.init()

// Create a form view:
gui.addView( 
	{ ... view config ... },
	{ ... plug in congig ... }
)
```

Full example: [simple form](https://github.com/ma-ha/easy-web-app/blob/master/examples/simple/index.js)
	
## 20 sec Test
Requires [node.ns installed](https://nodejs.org/en/download/) -- which is always a good idea to have it.

Get a local copy and start example:

```bash
git clone https://github.com/ma-ha/easy-web-app.git

cd easy-web-gui
npm install
 
cd examples
cd simple
nodejs index.js
```

Now open the web app in your browser: [http://localhost:8888/](http://localhost:8888/)
	
## First project (30 sec)
Requires [node.ns installed](https://nodejs.org/en/download/) -- it really don't hurt and it's always a good idea to have.

Create a demo folder and install _easy-web-app_ via _npm_

```bash
mkdir demo
cd demo
npm install easy-web-app
```

Create a _simpleForm.js_ file with following content (this is the [form example](https://github.com/ma-ha/easy-web-app/blob/master/examples/simple/index.js)):

```javascript
/** Simple example: Create a web page with form */
var gui = require ( 'easy-web-app' )

/** Initialize the framework and the default page */
gui.init ()

/**
 * Add a view of type "pong-easy-form" (= plug-in) to the default page the first
 * parameter of addView is the view configuration, a second parameter can define
 * the plug-in configuration, a third parameter can specify the page.
 */
gui.addView ( 
  {
    'id'   : 'myFirstView',
    'type' : 'pong-easyform'
  },
  {
    "id" : "tstFormId",
    "easyFormFields" : [ 
        "id"
      , "c1|Name"
      , "c1|Date|date"
      , "c1|separator"
      , "c1|Remark|3rows"
      , "c2|Mailings|label"
      , "c2|Send~Ads~~|checkbox_infomails_ads"
      , "c2|Newsletter|checkbox_infomails_newsletter"
      , "c2|Pass~Word" 
    ],
    "actions" : [ 
      {
        "id" : "Chk",
        "actionName" : "Check",
        "actionURL"  : "svc/test/check"
      }
    ]
  }
)
```

Run the demo:

	node simpleForm.js
	
Open the URL [http://localhost:8888/](http://localhost:8888/) in your Browser.

Remark: To keep this demo simple, there is no REST service backend for the 
"Chk" button implemented. 
Please have a look at the [I/O example](https://github.com/ma-ha/easy-web-app/blob/master/examples/io/index.js) -- 
this includes a fully working service backend.

## Examples
Have a look at some feature demos: 
* [Simple page with one web form](https://github.com/ma-ha/easy-web-app/tree/master/examples/simple)
* [Two page with navigation tabs](https://github.com/ma-ha/easy-web-app/tree/master/examples/multi-page)
* [Table demo](https://github.com/ma-ha/easy-web-app/tree/master/examples/table-demo)
* [Complex layout demo](https://github.com/ma-ha/easy-web-app/tree/master/examples/complex-layout)
* [I/O demo](https://github.com/ma-ha/easy-web-app/tree/master/examples/io)