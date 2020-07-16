# Markdown Usage

### Content

- Collapsible Tag
- Images on Single Line



### Collapsible Tag

#### Method

Just using HTML `<details>` Tag.

#### Usage

```
<details>
	<summary>Click to expand!</summary>

Here is your content !

</details>
```

#### Result

<details>
	<summary>Click to expand!</summary>

Here is your content !

</details>

### Images on Single Line

#### Method 1

Images as links.

#### Usage 

```
[![alt](image1 url)](link1 url)
[![alt](image2 url)](link2 url)
```

#### Result

[![GitHub icon](https://github.com/favicon.ico)](https://github.com/favicon.ico)
[![GitHub icon](https://github.com/favicon.ico)](https://github.com/favicon.ico)

#### Method 2

Using HTML and CSS

#### Usage

```
<img src="image1 url" width="" align="left"/>
<img src="image2 url" width="" align="left"/>
```

#### Result

<img src="https://github.com/favicon.ico" width="" align="left"/>
<img src="https://github.com/favicon.ico" width="" align="left"/>