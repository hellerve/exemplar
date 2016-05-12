# exemplar

This is a port of the [exemplar](https://github.com/lfex/exemplar) library
to zepto. It is more or less direct, but overcomes one or two of its'
awkwardnesses (and introduces another, yay).

# Usage

The port is compatible enough with the original version to look familiar.

````clojure
(load "exemplar/exemplar")

(++ (doctype) (html (-head) (body (p "i am some text"))))
; => <!DOCTYPE html>\n<html><head /><body><p>i am some text</p></body></html>
(link #{"href" "https://google.com"})
; => <link href="https://google.com">
```

To people who know exemplar, there should be a few things that are new:
1. Multiple child elements need not be wrapped in a list.
2. The attributes on the other hand are presented in the form of a hash map.
3. Elements that provoke nameclashes (namely: `head` and `map`) are prefixed with a hyphen.

This makes the code a bit easier to look at overall (or so I believe).

As in exemplar, one can also define one's own elements:

```clojure
(defelem fancy-custom-element)
(fancy-custom-element (p "i am inside a fancy elem"))
; => <fancy-custom-element><p>i am inside a fancy elem</p></fancy-custom-element>
```

To avoid nameclashes, one can also do a `render-as`-style call to `defelem`:

```clojure
(defelem fancy-custom-element "fce")
(fancy-custom-element (p "i am inside a fancy elem"))
; => <fce><p>i am inside a fancy elem</p></fce>
```

This is the reason why `-map` renders to `<map>`.

<hr/>

Have fun!
