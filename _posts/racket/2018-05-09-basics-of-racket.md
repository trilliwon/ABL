---
layout: post
title:  "Basics of Racket Programming"
date:   2018-05-09 16:00:00 +0900
tag: [Racket]
---

## Basics of Racket

---

## A program module is written as
- `#lang ‹langname› ‹topform›*`
- + one or more
- * zero or more
## Definitions
`( define ‹id› ‹expr› )`
`( define ( ‹id› ‹id›* ) ‹expr›+ )`

### Ex
```
(define pie 3)
(define (piece str)
  (substring str 0 pie))
  
  

(define (bake flavor)
  (printf "pre-heating oven...\n")
  (string-append flavor " pie"))

(bake "apple")

(define (nobake flavor)
  string-append flavor "jello")

(nobake "green") ; fails to include its argument should use ()
```


---

## Identifiers

- **( ) [ ] { } " , ' ` ; # | \**
- Racket’s syntax for identifiers is especially liberal. Excluding the special characters

---

## Function Calls

- `( ‹id› ‹expr›* )`
- `( ‹expr› ‹expr›* )`

```

(define (double v)
  ((if (string? v) string-append +) v v))


> (string-append "rope" "twine" "yarn")  ; append strings
"ropetwineyarn"

> (substring "corduroys" 0 4)            ; extract a substring
"cord"

> (string-length "shoelace")             ; get a string's length
8

> (string? "Ceci n'est pas une string.") ; recognize strings
#t

> (string? 1)
#f

> (sqrt 16)                              ; find a square root
4

> (sqrt -16)
0+4i

> (+ 1 2)                                ; add numbers
3

> (- 2 1)                                ; subtract numbers
1

> (< 2 1)                                ; compare numbers
#f

> (>= 2 1)
#t

> (number? "c'est une number")           ; recognize numbers
#f

> (number? 1)
#t

> (equal? 6 "half dozen")                ; compare anything
#f

> (equal? 6 6)
#t

> (equal? "half dozen" "half dozen")
#t

```

---

## Conditionals with if, and, or, and cond

- `( if ‹expr› ‹expr› ‹expr› )`

```
(if (> 2 3) "bigger" "smaller")

(define (reply s)
  (if (equal? "hello" (substring s 0 5))
      "hi!"
      "huh?"))

(reply "hello racket") ; hi!
(reply "λx:(μα.α→α).xx") ; huh?


(define (reply1 s)
  (if (string? s)
      (if (equal? "hello" (substring s 0 5))
          "hi!"
          "huh?")
      "huh?"))

(define (reply2 s)
  (if (if (string? s)
          (equal? "hello" (substring s 0 5))
          #f)
      "hi!"
      "huh?"))
```

---

## Anonymous Functions with lambda

- `( lambda ( ‹id›* ) ‹expr›+ )`

```
> (lambda (s) (string-append s "!"))
#<procedure>

> (twice (lambda (s) (string-append s "!"))
         "hello")
"hello!!"
> (twice (lambda (s) (string-append s "?!"))
         "hello")
"hello?!?!"

(define (make-add-suffix s2)
  (lambda (s) (string-append s s2)))
 
```

---

## Local Binding with define, let, and let*
- `( define ( ‹id› ‹id›* ) ‹definition›* ‹expr›+ )`
- `( lambda ( ‹id›* ) ‹definition›* ‹expr›+ )`
- `( let ( {[ ‹id› ‹expr› ]}* ) ‹expr›+ )`

```
> (let ([x (random 4)]
        [o (random 4)])
    (cond
     [(> x o) "X wins"]
     [(> o x) "O wins"]
     [else "cat's game"]))
"O wins"


; The bindings of a let form are available only in the body of the let, so the binding clauses cannot refer to each other. The let* form, in contrast, allows later clauses to use earlier bindings:


> (let* ([x (random 4)]
         [o (random 4)]
         [diff (number->string (abs (- x o)))])
    (cond
     [(> x o) (string-append "X wins by " diff)]
     [(> o x) (string-append "O wins by " diff)]
     [else "cat's game"]))
 "cat's game"
```


---

## Lists, Iteration, and Recursion
- The list function takes any number of values and returns a list containing the values:

```
> (list "red" "green" "blue")
'("red" "green" "blue")
> (list 1 2 3 4 5)
'(1 2 3 4 5)

> (length (list "hop" "skip" "jump"))        ; count the elements
3
> (list-ref (list "hop" "skip" "jump") 0)    ; extract by position
"hop"
> (list-ref (list "hop" "skip" "jump") 1)
"skip"
> (append (list "hop" "skip") (list "jump")) ; combine lists
'("hop" "skip" "jump")
> (reverse (list "hop" "skip" "jump"))       ; reverse order
'("jump" "skip" "hop")
> (member "fall" (list "hop" "skip" "jump")) ; check for an element
#f

```

---

## Predefined List Loops

### map
```
> (map sqrt (list 1 4 9 16))
'(1 2 3 4)
> (map (lambda (i)
         (string-append i "!"))
       (list "peanuts" "popcorn" "crackerjack"))
'("peanuts!" "popcorn!" "crackerjack!")


> (andmap string? (list "a" "b" "c")) ; string list
#t
> (andmap string? (list "a" "b" 6)) ; not string list
#f
> (ormap number? (list "a" "b" 6)) ; has number element
#t

> (map (lambda (s n) (substring s 0 n))
       (list "peanuts" "popcorn" "crackerjack")
       (list 6 3 7))
'("peanut" "pop" "cracker")

```

### filter
- The filter function keeps elements for which the body result is true, and discards elements for which it is #f:

```
> (filter string? (list "a" "b" 6))
'("a" "b")
> (filter positive? (list 1 -2 6 7 0))
'(1 6 7)
```

### foldl
- The foldl function generalizes some iteration functions. It uses the per-element function to both process an element and combine it with the "current" value, so the per-element function takes an extra first argument. Also, a starting "current" value must be provided before the lists:


```
> (foldl (lambda (elem v)
           (+ v (* elem elem)))
         0
         '(1 2 3))
14 ; 1 + 4 + 9
```

>Despite its generality, **foldl** is not as popular as the other functions. One reason is that **map**, **ormap**, **andmap**, and **filter** cover the most common kinds of list loops.

---

## List Iteration from Scratch

- `first`: get the first thing in the list; and
- `rest`: get the rest of the list.

```
> (first (list 1 2 3))
1
> (rest (list 1 2 3))
'(2 3)


> empty
'()
> (cons "head" empty)
'("head")
> (cons "dead" (cons "head" empty))
'("dead" "head")


> (empty? empty)
#t
> (empty? (cons "head" empty))
#f
> (cons? empty)
#f
> (cons? (cons "head" empty))
#t
```

```
(define (my-length lst)
  (cond
   [(empty? lst) 0]
   [else (+ 1 (my-length (rest lst)))]))
 
> (my-length empty)
0
> (my-length (list "a" "b" "c"))
3
(define (my-map f lst)
  (cond
   [(empty? lst) empty]
   [else (cons (f (first lst))
               (my-map f (rest lst)))]))
 
> (my-map string-upcase (list "ready" "set" "go"))
'("READY" "SET" "GO")
```

---

### Tail Recursion

```
(define (my-length lst)
  ; local function iter:
  (define (iter lst len)
    (cond
     [(empty? lst) len]
     [else (iter (rest lst) (+ len 1))]))
  ; body of my-length calls iter:
  (iter lst 0))
  
  
  (define (my-map f lst)
  (define (iter lst backward-result)
    (cond
     [(empty? lst) (reverse backward-result)]
     [else (iter (rest lst)
                 (cons (f (first lst))
                       backward-result))]))
  (iter lst empty))
It turns out that if you write

(define (my-map f lst)
  (for/list ([i lst])
    (f i)))

```

## Recursion versus Iteration

- iteration is just a special case of recursion

```

(define (remove-dups l)
  (cond
   [(empty? l) empty]
   [(empty? (rest l)) l]
   [else
    (let ([i (first l)])
      (if (equal? i (first (rest l)))
          (remove-dups (rest l))
          (cons i (remove-dups (rest l)))))]))
 
> (remove-dups (list "a" "b" "b" "b" "c" "c"))
'("a" "b" "c")

; *****
(remove-dups (list "a" "b" "b" "b" "b" "b"))
= (cons "a" (remove-dups (list "b" "b" "b" "b" "b")))
= (cons "a" (remove-dups (list "b" "b" "b" "b")))
= (cons "a" (remove-dups (list "b" "b" "b")))
= (cons "a" (remove-dups (list "b" "b")))
= (cons "a" (remove-dups (list "b")))
= (cons "a" (list "b"))
= (list "a" "b")
```


---

## Pairs, Lists, and Racket Syntax

- The cons function actually accepts any two values, not just a list for the second argument. 
- Thus, a value produced by cons is not always a list. In general, the result of cons is a **pair**. 

```
> (cons 1 2)
'(1 . 2)
> (cons "banana" "split")
'("banana" . "split")

```

- The name rest also makes less sense for non-list pairs; the more traditional names for first and rest are car and cdr, respectively. (Granted, the traditional names are also nonsense. Just remember that “a” comes before “d,” and cdr is pronounced “could-er.”)

```
> (car (cons 1 2))
1
> (cdr (cons 1 2))
2
> (pair? empty)
#f
> (pair? (cons 1 2))
#t
> (pair? (list 1 2 3))
#t


> (cons (list 2 3) 1)
'((2 3) . 1)
> (cons 1 (list 2 3))
'(1 2 3)

> (cons 0 (cons 1 2))
'(0 1 . 2)

```

---

## Quoting Pairs and Symbols with quote

```
> (list (list 1) (list 2 3) (list 4))
'((1) (2 3) (4))


> (quote ("red" "green" "blue"))
'("red" "green" "blue")
> (quote ((1) (2 3) (4)))
'((1) (2 3) (4))
> (quote ())
'()


> (quote (1 . 2))
'(1 . 2)
> (quote (0 . (1 . 2)))
'(0 1 . 2)

> (list (list 1 2 3) 5 (list "a" "b" "c"))
'((1 2 3) 5 ("a" "b" "c"))
> (quote ((1 2 3) 5 ("a" "b" "c")))
'((1 2 3) 5 ("a" "b" "c"))

```
>A value that prints like a quoted identifier is a _symbol_. In the same way that parenthesized output should not be confused with expressions, a printed symbol should not be confused with an identifier. In particular, the symbol (quote map) has nothing to do with the map identifier or the predefined function that is bound to map, except that the symbol and the identifier happen to be made up of the same letters.

```
> map
#<procedure:map>
> (quote map)
'map
> (symbol? (quote map))
#t
> (symbol? map)
#f
> (procedure? map)
#t
> (string->symbol "map")
'map
> (symbol->string (quote map))
"map"

> (car (quote (road map)))
'road
> (symbol? (car (quote (road map))))
#t

> (quote (road map))
'(road map)


; The quote form has no effect on a literal expression such as a number or string:

> (quote 42)
42
> (quote "on the record")
"on the record"

```

---

## Abbreviating quote with `'`

```
> '(1 2 3)
'(1 2 3)
> 'road
'road
> '((1 2 3) road ("a" "b" "c"))
'((1 2 3) road ("a" "b" "c"))

> (car ''road)
'quote
> (car '(quote road))
'quote


> (quote (quote road))
''road
> '(quote road)
''road
> ''road
''road

```

---

## Lists and Racket Syntax

- a reader layer, which turns a sequence of characters into lists, symbols, and other constants; and
- an expander layer, which processes the lists, symbols, and other constants to parse them as an expression.

```
> (+ 1 . (2))
3


> (1 . < . 2)
#t
> '(1 . < . 2)
'(< 1 2)

```

