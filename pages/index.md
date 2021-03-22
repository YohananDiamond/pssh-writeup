# Index

* [Possible names & stuff](possible-names.md)

## Ideas

```
# this is a comment!

# the code below shows "Hello, World!" on the screen.
$ print "Hello, World!"

# hmm... I don't like quotes. Let's try typing without them.
$ print Hello, World!
Error: unknown identifier: Hello,

# wait, what?
# Oh well, this shell won't support strings as-is. I feel like it makes
# things unsafe [TODO: tell why]

# By the way, notice the `,` is also part of an identifier!

# Defining functions
$ fn hello-world arg1 arg2
$     printfmt "Hello, World! {} + {} is {}" arg1 arg2 (arg1 + arg2)
$ end
(Value returned: <hello-world@0x3F8D96>)
$ let hello-world2 |arg1 arg2|
$     printfmt "Hello, World! {} + {} is {}" arg1 arg2 (arg1 + arg2)
$ end
(Value returned: <hello-world2@0x3F10C>)

# standard shell commands
$ shdo "echo" "Hello, World!" :shell "sh"
Hello, World!

# making paths (because using quotes for them would be terrible)
# TODO: not sure at all on this syntax
$ shdo "touch" "foo"
$ pathinfo @P:foo
(Value returned: std.path.PathInfo{:type .File})

# if branches!
$ let var = true
$ let foo = if var 20 else 50 end
$ foo
(Value returned: 20)

# this is valid:
$ print 10 + 5

# this is also valid:
$ print (10 + 5)

# this is not valid:
$ print 10 + 5 8
Parsing Error: ambiguous

# lambdas because we love them
$ let lambda 

# iteration with... lambdas? :O

# creating variables
$ let v = 50
$ print v
50

# mutable variables variables
$ mut v = 50
$ print v
50
$ v = 42
$ print v
42

# async commands
# TODO: think how this stuff will work lel
$ async || for (range 2) |x| printfmt "Hello from A! {}"; sleep 1; done; done
$ async || for (range 2) |x| printfmt "Hello from B! {}"; sleep 1; done; done
Hello from A! 0
Hello from B! 0
Hello from A! 1
Hello from B! 1

# TODO: expose pointers or something idk, I hate not having pointers in
# python

# TODO: structs (not classes!)
# TODO: shell piping, function piping, partial function application,
# non-function output piping

# semicolons at the end of the line are optional
# TODO: should I 
$ print "Hello, World";

# TODO: how to enforce error handling on a dynamically typed language

# TODO: typing? oh god... this might be hell.

# TODO: .MaybeUseThisEnumVariant or :this-might-be-more-fitting

# TODO: vectors and stuff for more efficient

# TODO: standard parsing module for calling from sh-like environments

# TODO: language-inside heredocs for multiline code without the \
forward-decl <-END
    :file ...
<-END

# kwcall!
fn soma-e-dobro x y
    return 2 * (x + y)
end
$ soma-e-dobro 10 20
(Returned: 60) [L1:soma-e-dobro 10 20]
$ kwcall soma-e-dobro {:x 10 :y 20}
(Returned: 60) [L2:kwcall soma-e-dobro {:x 10 :y 20}]

# Lazy imports and module declarations (@ prefix means builtin function, and they cannot be overriden)
# /usr/lib/pssh/std/startup.pssh
@pssh-module "PSSH Standard Library"

kwcall lazy-import {:file (@this-file + "/../print.pssh")
                    :identifiers ["print" "printfmt"]}

# captures (and mutable captures)
```

* Parsing modes: `--per-line` and `--entire` (where `--entire` is the
  default) (`--per-line` is useful when reading commands from standard
  input and should be enabled there by default).

<!--
  vim: ft=markdown
-->
