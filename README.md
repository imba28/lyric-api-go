# Lyric API written in Golang

[![GoDoc](https://godoc.org/github.com/imba28/lyric-api-go?status.svg)](https://godoc.org/github.com/imba28/lyric-api-go)

This library provides an API to search for lyrics from various providers.

## Supported Providers

- Genius (Requires Setup)
- SongLyrics (Default)

Please refer to the test files, examples, and [GoDoc](https://godoc.org/github.com/imba28/lyric-api-go) for more details
on using the providers.

## Installing

### using go get

```sh
go get github.com/imba28/lyric-api-go
```
### Getting Started

Give this library a spin,

```sh
git clone https://github.com/imba28/lyric-api-go.git
cd lyric-api-go
go run example/search.go
```

### Basic Usage

```go
package main

import (
    "fmt"

    "github.com/imba28/lyric-api-go"
)

func main() {
    var (
        artist = "John Lennon"
        song   = "Imagine"
    )

    l := lyrics.New()
    lyric, err := l.Search(artist, song)

    if err != nil {
        fmt.Printf("Lyrics for %v-%v were not found", artist, song)
    }
    fmt.Println(lyric)
}
```

### Using Only a Certain Provider

```go
package main

import (
    "fmt"

    "github.com/imba28/lyric-api-go"
)

func main() {
    var (
        artist = "John Lennon"
        song   = "Imagine"
    )

    l := lyrics.New(lyrics.WithoutProviders(), lyrics.WithGeniusLyrics("your_access_token_here"))
    // Use the following if you wish to just add Genius as a fallback
    // l := lyrics.New(lyrics.WithGeniusLyrics("your_access_token_here"))
    lyric, err := l.Search(artist, song)

    if err != nil {
        fmt.Printf("%v: Lyrics for %v-%v were not found", err, artist, song)
    }
    fmt.Println(lyric)
}
```

## Contributing

You are more than welcome to contribute to this project. Fork and
make a Pull Request, or create an Issue if you see any problem or want to propose a feature.
