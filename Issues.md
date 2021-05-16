# Stack: Loader
Get 'slash' handling documented and consistent in Loader implementations

# Design issues

## Shell contents

Need to rethink `jsh.shell.jsh.home`, `jsh.shell.jsh.src`, and the use of "source-level" plugins. Currently we are scanning the source directory for plugins in an unbuilt shell and relying on a manifest in `jsh/etc/api.js` for a built shell. The approaches should be harmonized in a way that makes sense:

* Do we need a way to have plugins that exist but are not included at runtime?
* Do we need the source code to be installed in a built shell and be available at runtime?
* Do we need that separate manifest at `jsh/etc/api.js` to remain, as well as the implied manifest at `jsh/etc/index.html`?

## Documentation

We should reconcile and unify the concept of a documented module. Currently `jsh/etc/api.js` and `jsh/etc/index.html` both have the concept of a jsh-documented API. Information about what a module does is stored in `jsh/etc/index.html` rather than closer to the code itself. We should come up with a better way for generating and linking this documentation that works for several scenarios:

* Local hosting, where someone is browsing a source checkout (possibly we could require an HTTP server if it were easy enough)
* Remote hosting, where someone is browsing source code online (e.g., at Bitbucket)
* Local build, where someone is browsing HTML generated at build time in a built shell.

# Integration issues

## Profiler / Nashorn

The profiler does not work when running under Nashorn; a NoClassDefFoundError is thrown for the profiler code from within Nashorn, although the agent runs until then and still emits output with its shutdown hook.

## jsh / Nashorn / NetBeans

The NetBeans JPDA debugger does not correctly step into some Nashorn-executed `jsh` internals due to NetBeans [issue 247441](https://netbeans.org/bugzilla/show_bug.cgi?id=247441).

# jsh.shell.jsh exit codes

Do jsh subshells created via jsh.shell.jsh but not forked all share the same exit status value because they rely on the Rhino shell variable for that purpose? Or is that in the launcher process and the loader process does not do that?

# Java logging

## Current state

Currently, Java logging can be configured in two ways. It can be configured on the command line using the ordinary Java mechanism - a properties file - that is specified as a jsh setting. Or, it can be installed at runtime using the js/debug implementation which uses JavaScript to implement logging.

## Ideas

It's hard to be sufficiently flexible using a single properties file. It's hard to easily manipulate, inherit, and so forth.

One solution would be to allow multiple properties files and cascade them, possibly using an index or something to indicate them (settings like jsh.log.java.properties.0, and so forth). This would be fairly simple to implement in the launcher and would provide more flexibility than the current situation.

Another solution would be to use JavaScript and load it into the loader, allowing a JavaScript configuration to somehow specify a series of properties that could be fed to the `java.util.logging` implementation. This could be loaded from the launcher and produce a properties file for the loader, or could be loaded within the loader.

A third solution is to provide an all-Javascript implementation of an object that configures the Java `LogManager`. A skeletal version of this is in place that reduces the logging implementation to a single JavaScript function (mapping to a Java `Handler`). A JavaScript object that provides more flexibility is probably the next step, allowing levels to be specified, potentially allowing filtering to be specified, to provide more performance-friendly possibilities.

# Browser integration

Browser integration is a mess; there is the concept of Google Chrome in the rhino/shell module, and a more generalized concept of a browser in the jsh/unit module; the new browser test suite runner uses an internal representation of a browser from jsh/unit and adds its own decoration on top of it. Unifying all of these concepts and taking the best of all of them would be much cleaner and would get rid of a lot of cruft.

# The loader/api module

(empty)

# Development

(empty)