# Roadmap #

## Engine Support ##

Nashorn is being considered for deprecation, according to [JEP 335](http://openjdk.java.net/jeps/335) (see also [InfoQ](https://www.infoq.com/news/2018/06/deprecate-nashorn)). [GraalVM](https://www.graalvm.org/) is being proposed as the alternative for writing hybrid Java/JavaScript applications. It is important to begin investigating GraalVM's capabilities to see how SLIME could run on it. See this [Twitter discussion](https://twitter.com/thomaswue/status/1004756104172228608) for some useful information.

## Older Proposed Releases (obsolete?) ##
### 0.0.4.9 ###

The 0.0.4.9 release will center around ease of deployment.

* HTTP delivery of scripts; allowing execution over the Internet
* Add support for CoffeeScript (#141)
* Improved pre-release automated testing

### 0.0.5 ###

The 0.0.5 release will solidify the API and documentation. It will include:

* The ability to bootstrap the shell when the code is hosted on an HTTP server
* Easier development of API tests
* Adding support for Nashorn (#158)
* Better native launcher; see #21, #56, and #58.