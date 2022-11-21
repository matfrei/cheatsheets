# Useful regex commands


## Emacs regex

### Replace one latex formula by another
```
find:
\custom_nabla
\\mathop{\\nabla}[ ]*\\limits_{\(.*?\)}[ ]*\([a-zA-Z]\)
replace:
\custom_nabla1
\\mathop{\\nabla}[ ]*\\limits_{\(.*?\)}[ ]*\\negthickspace[ ]*\([a-zA-Z]\)
```

### Replace ugly \hl comments with custom macro
```
find:
\\hl{\(.*?\)}
replace:
\\owntodo{\1}
```
