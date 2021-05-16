# Things to think about that are insufficiently specific to be treated as issues.

* Tests for backward compatibility when running a source distribution. We can check out old code and run the tests and make sure they still pass.

* Loader improvements
    * Consider deprecating jsh.loader.run, jsh.loader.file, jsh.loader.module, inonit.loader.run, inonit.loader.file, inonit.loader.module and replace with jsh.file.Loader.run(…) etc. and no replacement for browser (Loader constructor)
    * Consider merging inonit.loader.run and inonit.loader.value and making the inonit.loader.value behavior the default
* MIME and Resource improvements
    * Need to go through the various places touched by the concept of resource and think through how to handle MIME types.
    * Probably need to add a MIME package for creating MIME multipart requests and guessing MIME types from names and content
    * Probably also need a MIME message parser
    * Should plug MIME message parser into the servlet package to handle things like file uploads

* The JSH_SCRIPT_CLASSPATH and JSH_PLUGINS concept both can add Java classes to the classpath, but do so differently. Should JSH_PLUGINS add all classes to the jsh loader classloader and should we remove the concept of JSH_SCRIPT_CLASSPATH? For example, scripts that attempt to load JavaMail as a plugin fail when sending some messages with the "No object DCH" error. *(The JavaMail issue may have been fixed in a subsequent release by loading classes using a better ClassLoader implementation.)*

* Launcher improvements
    * Idea: C launcher could invoke Java command and somehow detach it, rather than linking to the JVM
    * Idea: launcher could be invoked by C launcher and return data, which then could be used to invoke other launcher, so C launcher could get away without implementing the logic of the Java launcher but not produce a subprocess
    * get jsh launcher to run a program to get settings and then launch jsh; one Java process, not two
    * Idea: Launcher is already loading and preprocessing code; could send it to the loader through stdin, possibly, although then the loader would have to know when the code ended and something else began.

* Profiler improvements
    * It appears it should be possible to use the profiler without Javassist, and profile only script methods
    * Consider providing backtraces for hotspots

* Servlet improvements
    * Provide the ability to implement a `com.sun.net.httpserver`-based server without Tomcat or the Servlet API being installed
    * Make sure that support for HTTP and HTTPS is provided by the jsh servlet plugin integration with Tomcat