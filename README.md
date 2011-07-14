# println

[println](http://println.io) is a blogging / publishing software written in [Scala](http://www.scala-lang.org) with the [Lift Web Framework](http://www.liftweb.net). It tries to fulfill the need for an un-obustrive approach of writing, publishing and managing ones blog posts with it's overlay-editor-window.

It is heavily inspired by [Nesta CMS](http://nestacms.com/) a Ruby based CMS Software and also uses parts of its default layout (since i like it for its simplicity).

The official website is currently being done with println itself, please be patient as it well well-done. There will also be a webcast soon.


## Features

* High Performance (thanks to Lift and Scala)
* Easy to use (thanks to me)
* Easy to customize (by default only layout or css changes are needed)
* Easy to deploy (.war Archive)
* Internal web-tracking with MongoDB
* Lots of widgets by default

It is made with the following pieces of software:

* [Scala](http://www.scala-lang.org) Programming Language
* [Lift Web Framework](http://www.liftweb.net)
* [jQuery UI](http://www.jqueryui.com) Dialog
* modified Version of [WMD MarkDown-Editor](https://github.com/klipstein/wmd) with Live-Content-Preview


## How to get started

In order to get, compile and run the project locally, you need:

* git of course
* [simple-build-tool](https://github.com/harrah/xsbt/wiki)
* [PostgreSQL](http://www.postgresql.org) for Content-Storage ([check alternatives](http://www.assembla.com/spaces/liftweb/wiki/Persistence_Alternatives))
* [mongoDB](http://www.mongodb.org) for Statistics (optional)


After installing PostgreSQL, run the following in your shell:

```shell
$ createuser -Upostgres printlndemo
$ createdb -Upostgres --owner println printlndemo
```


If everything is up and running:

```shell
$ git clone git://github.com/fbettag/println.git
$ cd println
$ edit src/main/resources/props/default.props (or production.props)
$ ./sbt update
$ ./sbt ~jetty-run
```

Visit http://127.0.0.1:8080 with your browser and follow the on-screen instructions.


## Without MongoDB

MongoDB is soley used for statistical analysis like Browser-, Referer- or Target-URL-tracking. This is not fully tested yet, but it has interesting results and more flexibility as opposed to other commercial products.

If you want to try this project without MongoDB, feel free to do so. Just make sure you set "useMongoDB_?" to false in Boot.scala.


## Tracking atom.xml and sitemap.xml

Simply place the following in one or both of the files (not in any of the repeated sections of course):

<code>
<lift:Stats.track/>
</code>


## Layout and Widgets

The main layout is in src/main/webapp/template-hidden/default.html and has all the widgets that are currently implemented. Here is the overview:

* BitPit: <span class="lift:Helpers.bitpit?id=7019"/>
* Twitter: <span class="lift:Helpers.twitter?user=fbettag"/>
* Google Analytics: <span class="lift:Helpers.analytics?ua="/>
* Copyright Helper: &copy; <span class="lift:Helpers.years?since=2010"><span id="copyright_years"></span></span>

If you want to implement your own, feel free to look at src/main/scala/code/snippets/Helpers.scala for how to do so.


## Todo

* XmlResponse for "post" needs a Sitemap. ("No navigation defined"-error) http://groups.google.com/group/liftweb/browse_thread/thread/18d4334601bacf57
* jQuery Dialog for adding new posts with auto-slugging ([a-zA-Z0-9/,-]) http://groups.google.com/group/liftweb/browse_thread/thread/d42aaa377f62f12f
* Blog.scala:68 Only show many-to-many posts according to User-status
* jquery.tokeninput.js:641 Fix the dropdown to be selectable by keyboard
* println.js:153 Save window-size in a Cookie, make wmd-textarea auto-resizable with jQueryUI dialog
* Tagging -> return way to server
* Twitter, Facebook and Google+ Integration
* grep for FIXME or FIXIT ;)


## Footnote

Thanks to everybody in the Lift Community and on [Liftweb Google Groups](http://groups.google.com/group/liftweb).