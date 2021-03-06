# backoff

[![GoDoc](https://godoc.org/github.com/cenkalti/backoff?status.png)](https://godoc.org/github.com/cenkalti/backoff)
[![Build Status](https://travis-ci.org/cenkalti/backoff.png)](https://travis-ci.org/cenkalti/backoff)

This is a Go port of the exponential backoff algorithm from
[google-http-java-client](https://code.google.com/p/google-http-java-client/wiki/ExponentialBackoff).

[Exponential backoff](http://en.wikipedia.org/wiki/Exponential_backoff)
is an algorithm that uses feedback to multiplicatively decrease the rate of some process,
in order to gradually find an acceptable rate.
The retries exponentially increase and stop increasing when a certain threshold is met.




## Install

```bash
go get github.com/cenk/backoff
```

## Example

Simple retry helper that uses exponential back-off algorithm:

```go
operation := func() error {
    // An operation that migth fail
}

err := backoff.Retry(operation, backoff.NewExponentialBackoff())
if err != nil {
    // handle error
}

// operation is successfull
```
