# Markdown Usage Anchors

## Header Really Represent In Markdown

```
# Hello World
```

Represent to 

```
<a href="#hello-world" id="hello-world" class="anchor" aria-hidden="ture">Hello World</a>
```

## Anchors

As a Anchor:

- Markdown header `### anchor`
- HTML header `<h1>anchor</h1>`
- HTML link `<a name="anchor">`, or `<a id="anchor">`

## Links

Link Destination can be ignore English lowercase, uppercase, and special character.

- `[Hello World](#hello-world)`
- `[Hello World](#Hello-World)`
- `[Hello World](#Hello World)`

## Examples of Link to Anchors

Link to Markdown header `###`

```
[Hello World](#hello-world)
...
### Hello World
...
```

Link to Markdown header `###` (contains special characters)

```
[Ready, set, GO!](#ready-set-go)
...
### Ready, set, GO!
...
```

Link to HTML header `<h1>`

```
[Hello World](#hello-world)
...
<h3>Hello World</h3>
```

Link to HTML link `<a name="">`

```
[Hello World](#hello-world)
...
<a name="hello-world">Hello World</a>
```



---

## Test Area

## Links

1. link to `###`

[Hello World](#hello-world)

[Ready, set, GO!](#ready-set-go)

2. link to `<h>`

[html header](#html header)

3. link to `<a>`

[a-name](#a-name)

[a-id](#a-id)



---



























---

## Anchors

1. ###

### Hello World

### Ready, set, GO!

2. `<h>`

<h3>HTML Header</h3>



3. `<a name=''>`

<h3><a name="a-name">a-name-anchor</a></h3>



<a id="a-id">a-id-anchor</a>

...











...













...

--END--