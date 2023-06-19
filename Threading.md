# Threading

There is a newer loader implementation at `slime.loader.runtime.Synchronous`. The asynchronous version of the newer API is not yet
implemented.

An older synchronous/asynchronous API exists as `slime.old.Loader`.

| Platform      | Loader: Synchronous      | Loader: Asynchronous             |
| --------      | ------------------------ | -------------------------------- |
| Rhino         | Yes                      | Unimplemented                    |
| Nashorn       | Yes                      | Unimplemented                    |
| Browser       | Yes, uses deprecated API | Old version implemented. Tested? |
| GraalVM       | ?                        | ?                                |
| Node.js       | Yes, filesystem-based    | No                               |
