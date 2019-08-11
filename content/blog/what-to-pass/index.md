---
title: "What to Pass: a Var or IFn?"
date: 2015-08-23T12:33:14-06:00
tags: ["clojure", "code"]
---
## Mapping a function over a channel

You have a function you are developing:

```
(defn name-string
  "Gives you the name string from a suitable map"
  [{:keys [first-name]}]
  first-name)
```

and you want to run this on maps you get over, say, a socket. Thus you shove it up a channel with an attached transducer of `(map name-string)` (or with a pipeline of the actual data channel, for the indirection).
## A Problem Arises

Now, you want to incorporate the last name as an initial. Thus:

```
(defn name-string
  "Gives you a first name with a last name initial"
  [{:keys [first-name last-name]}]
  (str first-name \space (first last-name) "."))
```
But, oh noes! The old definition is still used. Naïvely you would restart the input source (or if you did use indirection, point it to a new channel). There is a better way, for development purposes. This does incur a small overhead and allows a feature which may be a security hole in production.
## What is `a-function`

This will resolve at compile time to the current value of the var named by the symbol (or just the value bound to it if a local). This is usually an IFn instance if it's a function. This works fine and dandy in a language with no runtime definitions—*cough* java *cough*—but it falls flat when used in a dynamic language. It is consistent and logical, unfortunately it does sometimes surprise people when redefinitions do nothing.
## What Is #'a-function

At read time this will turn to `(var a-function)`. At runtime it evaluates to a `clojure.lang.Var` object if a-function is a global. The meta-magic here is that `Var` implements `IFn`, and if it's a var for a function, invoking the var will invoke the function the var currently points at. I can hear thosee of you saying "that's a reference," and you are indeed correctish. `Var`s are one in the sense they allow mutability, but they also don't allow much else. You can also change the root binding atomically (I think), and if it is marked dynamic (by having `:dynamic true` in the metadata) you can change the current thread binding for a function call.
## Just Show Me The Codes!

```
(require '[clojure.core.async :as a])
;=> nil

(defn my-char
  [x]
  (char x))
;=> #'user/my-char

(def ch (a/chan 1 (map my-char)))
;=> #'user/ch

(a/>!! ch 97)
;=> true

(a/<!! ch)
;=> \a

; now let's redefine our function

(alter-var-root #'my-char comp inc)

; now it incs the number before turning it to a character

(a/>!! ch 97)
;=> true

(= \b (a/<!! ch))
;=> false

; oh noez! press the panic button!

; or do this when creating the channel

(defn my-char
  [x]
  (char x))
;=> #'user/my-char

(def ch (a/chan 1 (map #'my-char)))
;=> user/ch

(a/>!! ch 97)
;=> true

(= \a (a/<!! ch))
;=> true

(alter-var-root #'my-char comp inc)
;=> an instance of IFn

(a/>!! ch 97)
;=> true

(= \b (a/<!! ch))
;=> true

; yay!
```
