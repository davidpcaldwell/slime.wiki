# Roadmap

## Upcoming releases

[Milestones](https://github.com/davidpcaldwell/slime/milestones?direction=asc&sort=title&state=open)

## Engine Support

Nashorn has been deprecated. [GraalJS](https://www.graalvm.org/latest/reference-manual/js/) is proposed as the alternative for writing hybrid Java/JavaScript (along with other
languages) applications for the JVM. GraalJS's multithreading capabilities are substantially different from Rhino's, so in order to
fully support `jsh` on GraalJS, some work is required. See the [issue list](https://github.com/davidpcaldwell/slime/issues?q=is%3Aissue%20state%3Aopen%20graal%20label%3Agraal) for
details.

## Tool Integration Support

We can monitor the usage of development tools with which we integrate with a few tools:

* [Stack Overflow Developer Survey](https://survey.stackoverflow.co/2024/)
* [JetBrains State of Developer Ecosystem](https://www.jetbrains.com/lp/devecosystem-2023/)
