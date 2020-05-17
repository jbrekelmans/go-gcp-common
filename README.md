# Introduction
A collection of Go libraries.

# Index
1. [auth/google/compute](auth/google/compute): verification of Google Compute Engine identity JSON Web Tokens (see [Google's documentation](https://cloud.google.com/compute/docs/instances/verifying-instance-identity#verify_signature)). This is useful for applications that want to accept an authentication mechanism based on Google Cloud Platform's Identity Access Management infrastructure.
1. [cache](cache): a cache for values that need to be periodically re-evaluated where evaluations are expensive enough to justify ensuring only one Goroutine evaluates while other Goroutines wait for the evaluation. This primitive is useful for caching remote resources, such as JWKS' and authentication tokens, and supports the [context package](https://golang.org/pkg/context/).
1. [http](http): primitives focused around [RFC6750](https://tools.ietf.org/html/rfc6750). This is useful for HTTP servers that want to implement the Bearer authentication scheme.
1. [test](test): logrus logging in tests. For example:
    ```go
    import "github.com/jbrekelmans/go-lib/test"
    
    func Test_MyTest(t *testing.T) {
        defer test.RedirectLogs(t).Dispose()
        // Any calls that MyTest makes to logrus's standard logger are forwarded to t.Logf.
        MyTest()
    }
    ```
