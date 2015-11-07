---
layout: post
title:  "Markdown tests"
date:   2015-11-06 17:36:00
categories: tests
---

## Markdown is cool

I'm really linking this new markdown thing. Taks a little tweaking and getting
used to but it's kind of awesmome. So easy to read!

### Quoting

You can quote stuff:

> We choose to go to the moon, not because it's easy, but because it's hard.

### Listing

Apparently bullet lists should use `-` but not `+` or `*`:

- `-` is common
- `+` is wierd
- `*` can be confused with *italic*
    - although it does kind of look like a bullet
    - but KISS is still more important
        - right?
            - gosh so many bullet levels

Numered lists however

1.  should

    only

1.  use

        1.

1.   because it's better for **many** reasons


### Code blocks

Code blocks are important too. *E.g.*:

    echo 'This is a code block'

or a python example:

``` python
print 'This is also {0} code block'.format('a')
sys.exit()
```

Oops, doesn't work. I can't specify the language... What's up? Use this code to blow up your PC:

``` bash
sudo rm -rf /
```

so don't do it!

### Tables

We can even do tables! *How* awesome is this thing?

| h    | Long header |
|:-----|-------------|
| abc  | def         |
| abc2 | def2        |

Let's try again:

First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  | Content Cell

### Math

That's important too for \\(f(x)\\):

<div>
$$
\begin{align}
f(x) &= \int_{\tau=0}^{\infty} \tilde{f}(\tau)e^{i \omega \tau} d\tau
\end{align}
$$
</div>

### Superscript, underline

Yup, 10 m^2 is a surface. Want a 2^(nd)? Nah... Gotta talk about _underlining_.
