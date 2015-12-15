# Python embedded in all text formats by Emacs

`python-embedded.el` is a elisp file that evaluates python commands inside any file.

## Dependences

- emacs
- python

## Setup

Copy file to emacs folder: `cp python-embedded.el ~/.emacs.d/python-embedded/`

Add next lines to `init.el`:

```
(add-to-list 'load-path "~/.emacs.d/python-embedded")
(load "python-embedded.el")
```

By default `python-embedded.el` uses python3. You can change this replacing all

```
(ansi-term "/usr/bin/python3" "Python-IO")
```

with

```
(ansi-term "/usr/bin/python" "Python-IO")
```

## Example

Open `sample.py.html`

```html
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head>
    
  </head>
  <body>
    <p>The square of 11 is: «« 11**2 »»</p>
  </body>
</html>
```

Start python terminal: `M-p M-t` or `M-x pytex-start-python-term`

Eval all '««' '»»' environments: `M-p M-a` or `M-x pytex-to-tex-all`

`sample.py.html` changes to:

```html
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head>
    
  </head>
  <body>
    <p>The square of 11 is: «« 11**2 #= 121 »»</p>
  </body>
</html>
```

Export file: `M-p M-e` or `M-x pytex-export` then press `M-n` and RET

This saves `sample.html` file:

```html
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head>
    
  </head>
  <body>
    <p>The square of 11 is: 121</p>
  </body>
</html>
```