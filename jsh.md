# jsh #

`jsh` is a JavaScript environment for writing shell scripts. It runs on the Java virtual machine and requires at least Java 6 to be installed. (One recent release, jsh 0.0.4.8, has a bug that requires it to be running under a JDK, rather than merely a JRE, to start correctly.)

The following configurations are currently tested (note that "JDK" refers to Oracle's JDK):

Operating System     | Java version(s)              | JavaScript Engine(s) | Browser(s) | Native Launcher
-------------------- | ---------------------------- | -------------------- | --------------- | -------------
Mac OS X 10.10        | Oracle JDK 8u92 | [Rhino](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/Rhino), [Nashorn](http://openjdk.java.net/projects/nashorn/) | Safari 9.1.2, Google Chrome | No
Windows 7            | Oracle JDK 8u102              | Rhino, Nashorn | Internet Explorer 11 | No
Linux (Ubuntu 16.04) | OpenJDK 8u91                 | Rhino, Nashorn | Firefox | No

To install `jsh`, download the appropriate `-setup.jar` program from the [Downloads](../downloads) page and execute it using `java -jar jsh-[version]-setup.jar`.

The installer installs a Rhino-based `jsh`. The Nashorn-based `jsh` can be used by setting the `JSH_ENGINE` environment variable to `nashorn`.

For the upcoming 0.0.5 release, a new installer is used that runs directly from the web. It can be invoked with:
```
#!bash
jrunscript -e "load('https://bitbucket.org/api/1.0/repositories/davidpcaldwell/slime/raw/0.0.5/rhino/jrunscript/api.js?jsh/install')" <destination-directory>
```

`0.0.5` represents the version to install, and is a bookmark corresponding to the latest 0.0.5 release candidate that has passed the verification suite. The version may be specified by a commit ID, bookmark, or tag.

Beginning with 0.0.5, it is also possible to run a `jsh` script without installing `jsh` using an experimental interface for that purpose. A script may be run with the following (experimental) command:

```
#!bash
jrunscript -e "load('https://bitbucket.org/api/1.0/repositories/davidpcaldwell/slime/raw/0.0.5/rhino/jrunscript/api.js?jsh')" <script>
```

The name `0.0.5` is a version (commit, bookmark, or tag). `<script>` may be a local filename or a URL.