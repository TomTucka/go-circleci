## go-circleci

Go library for interacting with [CircleCI's API](https://circleci.com/docs/api). Supports all current API endpoints allowing you do do things like:

* Query for recent builds
* Get build details
* Retry builds
* Manipulate checkout keys, environment variables, and other settings for a project

**The CircleCI HTTP API response schemas are not well documented so please file an issue if you run into something that doesn't match up.**

Example usage:

```golang
package main

import (
        "fmt"

        "github.com/jszwedko/go-circleci"
)

func main() {
        client := &circleci.Client{Token: "YOUR TOKEN"} // Token not required to query info for public projects

        builds, _ := client.ListRecentBuildsForProject("jszwedko", "circleci-cli", "master", "", -1, 0)

        for _, build := range builds {
                fmt.Printf("%d: %s\n", build.BuildNum, build.Status)
        }
}
```

For the CLI that uses this library (or to see more example usages), please see
[circleci-cli](https://github.com/jszwedko/circleci-cli).

See [GoDoc](http://godoc.org/github.com/jszwedko/go-circleci) for API usage.

Feature requests and issues welcome!
