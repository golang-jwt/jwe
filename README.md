# jwe

[![build](https://github.com/golang-jwt/jwe/actions/workflows/build.yml/badge.svg)](https://github.com/golang-jwt/jwe/actions/workflows/build.yml)
[![Go Reference](https://pkg.go.dev/badge/github.com/golang-jwt/jwe.svg)](https://pkg.go.dev/github.com/golang-jwt/jwe)

A [go](http://www.golang.org) (or 'golang' for search engine friendliness)
implementation of [JSON Web
Encryption](https://datatracker.ietf.org/doc/rfc7516/). This is a companion
package to https://github.com/golang-jwt/jwt. A common use-case is to encrypt
the contents of a JWT using JWE.

## Disclaimer

The public API of this package is highly unstable and we are nowhere near any
stable `v1.0` version, so expect a number of breaking changes as we develop it.

Currently, this package is considered mostly a pet project, so please be aware
that the `golang-jwt` maintainers can only spent a limited time on this.
Therefore, any response to a pull request review might take some time. On the
other hand, we might be a little more lax with regards to API breaking pull
requests, as long as we are still in the `v0.x` version range.

## Usage

In order to build a new JWE, which encrypts a certain payload the function
`NewJWE` should be used.

```golang
import "github.com/golang-jwt/jwe"

func main() {
    originalText := []byte("The true sign of intelligence is not knowledge but imagination.")
    token, err := jwe.NewJWE(jwe.KeyAlgorithmRSAOAEP, pk, jwe.EncryptionTypeA256GCM, originalText)
    if err != nil {
        panic(err)
		return
	}

    compact, err := token.CompactSerialize()
	if err != nil {
        panic(err)
		return
	}
}
```
