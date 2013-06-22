go-httptimeoutclient
====================

A simple wrapper around http.Client to provide for timeouts

```Go
/*
    This wrapper takes care of both the connection timeout and the readwrite timeout.
    WARNING: You must instantiate this every time you want to use it, otherwise it is 
    likely that the timeout is reached before you actually make the call.

    One argument sets the connect timeout and the readwrite timeout to the same value.
    Other wise, 2 arguments are 1) connect and 2) readwrite

    It returns an *http.Client
*/

package main

import(
    httpclient "github.com/dmichael/go-httptimeoutclient"
    "time"
    "fmt"
)

func main() {
    httpClient := httpclient.NewTimeoutClient(500*time.Millisecond, 1*time.Second)
    resp, err := httpClient.Get("http://google.com")
    if err != nil {
        fmt.Println("Rats! Google is down.")
    }
    fmt.Println(resp)
}

```