# **MarkDown Cheat Sheet File**

> __Note:__ Html tags can be used in Markdown.

<!--comments-->
## Comments
<\!-- This is comment -->

\[comment]: <> (This is also a comment)

\[//]: <> (This is also a comment.)

\[//]: # (This is also a comment.)

---
<!-- Headings -->
## Headings

# Heading 1
\# Heading 1

## Heading 2
\## Heading 2

### Heading 3
\### Heading 3

#### Heading 4
\#### Heading 4

##### Heading 5
\##### Heading 5

###### Heading 6
\###### Heading 6

---
## Font Stylings
<!-- Italics -->
### Italics
\*This style* produces *italic*

\_This style_ produces _italic_

<!-- Strong -->
### Strong/Bold
\*\*This style** produces **Bold**

\_\_This style__ produces __Bold__

<!-- Strikethrough -->
### Strikethrough
\~~This style~~ produces ~~strike through~~


---
<!-- Horizontal Rule -->
## markdown Styles
### Horizontal Rule
\--- produces:

---

\___  produces:
 ___

<!-- Blockquote -->
### Blockquote
\> This is a quote and produces

> Quote

<!-- Links -->
### Links
\[link](http://www.link.com)

produces:

[link](http://www.link.com)

<!-- Images -->
### Images
\!\[Markdown Logo](https://markdown-here.com/img/icon256.png)

produces:

![Markdown Logo](https://markdown-here.com/img/icon256.png)

---
## Code Block
### Inline Code Block
<!-- Inline Code Block -->
\`This is a Inline code block`

which produces

`This is a Inline code block`

<!-- Code Blocks -->
### Code Blocks [*Github*]
> Note: code syntax highlighting is done when language name is given right after block start

> like: ```language name
```
    ```bash
    npm install
    npm start
    ```
```
produces:

```bash
  npm install
  npm start
```


#### Other examples

Javascript
```
    ```javascript
    function add(num1, num2) {
        return num1 + num2;
    }
    ```
```

```javascript
function add(num1, num2) {
    return num1 + num2;
}
```

Python

```
    ```python
    def add(num1, num2):
        return num1 + num2
    ```
```

```python
  def add(num1, num2):
    return num1 + num2
```

---
## Lists

<!-- UL -->
### Unordered list
\* produces List Item like below

* List Items
* List Items
  * Nested List Items
  * Nested List Items
  >Note: Nested List Items have different spacings Than parent list Items.


<!-- OL -->
### Ordered list
\1.

\1. produces List Item like below
1. List Item
1. List Item
1. List Item

> Note: can keep using '1.' for ordered list mark down will give correct order name.

### Tables [*Github*]
<!-- Tables -->
```
| First Name   | Last Name   |
| ------------ | ----------- |
| First Name 1 | Last Name 1 |
| First Name 2 | Last Name 2 |
```
will produce

| First Name   | Last Name   |
| ------------ | ----------- |
| First Name 1 | Last Name 1 |
| First Name 2 | Last Name 2 |

<!-- Task List -->
### Task List/CheckBox [*Github*]
```
* [x] Task 1
* [x] Task 2
* [ ] Task 3
```

Will produce
* [x] Task 1
* [x] Task 2
* [ ] Task 3
