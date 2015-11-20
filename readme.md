# Cub Widget

Cub Widget is a lightweight JavaScript application which can be installed
on any site. It has two main features:

* Add Users Login and Registration to your site and make it connected to 1.8m
  users of united users database of Praetorian Digital sites network;
* Collect data from various Lead Forms and send them to the central Praetorian
  Digital Leads database for processing.

The widget is implemented in pure JavaScript, and talks to a central database
directly from browser via Cub API. Basic widget integration requires no server
programming, so you can add it literaly on any site with minimal efforts.
If you need more sophisticated integration options - we have them, too.

### How it works

Widget is loaded on a page with a piece of JavaScript, like this (example):

```html
<script>
  var cubAsyncInit = function(cub) {
    // Configuration parameters
    cub.setup({
      apiKey: '<your-public-API-key>'
    });
    cub.start();
  };

  // Load Cub widget asynchronously
  (function(){
    if (document.getElementById("cub-widget-script")) {return;}
    var firstScript = document.getElementsByTagName("script")[0];
    var cubJs = document.createElement("script");
    cubJs.id = "cub-widget-script";
    // See notes about widget versioning
    cubJs.src = "//cub-praetorian.netdna-ssl.com/cub-widget.js";
    firstScript.parentNode.insertBefore(cubJs, firstScript);
  }());
</script>
```

When loaded, widget adds an interaction to the web page, either by rendering
extra interactive elements on it, like Login and Registration forms, or by
connecting to your existing HTML markup, like it does for Lead Forms. Widget
takes configuration parameters via ``cub.setup()`` method. Required parameter
for all actions is ``apiKey``. Before you can use the widget, you have to
register your application in Cub Admin and get an API key.

Please follow these links for detailed usage instructions:

* [Users Login and Registration](https://github.com/praetoriandigital/cub-docs/blob/master/registration.md)
* [Lead Forms](https://github.com/praetoriandigital/cub-docs/blob/master/forms.md)

### Browser compatibility

Widget is out-of-the box compatible with IE9+, Chrome, FireFox and Safari. If
you need IE8 compatibility, include
[ES5-shims](http://github.com/es-shims/es5-shim) on your page and widget will
work with IE8 too. Please note that shims must be loaded before widget script.

### Widget versioning

Widget versions follow [Semantic Versioning](http://semver.org). You can
check current version in browser console as ``cub.version``. Changes in public
widget API or documented behavior result in major or minor version change,
and bugfixes or internal widget improvements come as patch versions.

Widget script is distributed with MaxCDN using ``cub-praetorian.netdna-ssl.com``
domain. It supports both HTTP and HTTPS. It is strongly recommended that you
always use this distribution when including widget on your site, since it comes
with automatic updates and bugfixes. Two options of widget CDN distribution are
available:

1. Always latest version - recommended if you use Lead Forms feature only:

   <https://cub-praetorian.netdna-ssl.com/cub-widget.js>

2. Fixed major and minor version number, always latest patch version -
   recommended if you use Users Login and Registration and applied custom
   styling to it:

   <https://cub-praetorian.netdna-ssl.com/cub-widget.0.9.x.js>

Second option allows you to freeze any updates to widget HTML markup, its API
and documented behaviour, however you will still receive bugfixes as patch
versions until major or minor version changes. Please note that we ship
bugfixes for latest widget version only, so if you're using fixed widget
version you should update it yourself as new versions come out.

### Changes

* 0.9.x, November 2015
  - My Profile upgrade: added users photo upload, added Experience
    section;
  - change in registration flow: after registration users are now by default
    redirected to My Profile;
  - newsletter subscriptions during registration are now implicit;
  - Lead Forms feature added.
* 0.8.x - introducing Mailing List Subscriptions
* 0.7.x - load site configuration from API
* 0.6.x - introducing localStorage cache

### Troubleshoouting

Cub Widget makes its best to be developer-friendly and reports its errors and
warnings into your browser console. If something goes wrong, please check
messages in browser console first. If that doesn't help, or you found a bug,
or you'd like to suggest a feature - please feel free to open an
[Issue on Github](https://github.com/praetoriandigital/cub/issues).
