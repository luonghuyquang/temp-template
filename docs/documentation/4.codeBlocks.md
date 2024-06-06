---
title: Code blocks
---
# Code blocks
## Making Code blocks
!!! 
Making code blocks with 3 backticks ``` better supported (more features) than by indentation.  
!!! info "documentation: Code block"
    Documentation for <a href='https://squidfunk.github.io/mkdocs-material/reference/code-blocks/' target='_blank'> code blocks</a>

## Code copy and paste
!!! info "documentation: Code copy button"
    MkDocs-material <a href='https://squidfunk.github.io/mkdocs-material/reference/code-blocks/#code-copy-button' target='_blank'>Code copy button</a>  
```yaml title="mkdocs.yml"
theme:
  features:
    - content.code.copy
```

## Code line numbering
!!! info "documentation: adding line number for the code blocks by ```"
    MkDocs-material <a href='https://squidfunk.github.io/mkdocs-material/reference/code-blocks/#adding-line-numbers' target='_blank'>Adding line numbers</a>  
    This add line numbers to specific blocks with this only.
    ```js title=""
    linenums="1" // (1)!
    ```
    
    1. add this code after the 3 backtick (e.g. ``` linenums="1")

!!! info "adding line number for the code blocks by indentation"
    Method for adding line numbers different for the case of code block by indentation (4 indents in each line).  
    Add the following code to mkdocs.yml

???+warning
    This option will add line numbers to all code blocks.
    To selectively add line numbers to a particular blocks, use the above method.
    ```yaml title="mkdocs.yml" linenums="1"
    markdown_extensions:
      - codehilite:
        linenums: true # this is required for the code block by indentation only
    ```

## Highlight entire row of code
!!! info "documentation"
    MkDocs-material <a href='https://squidfunk.github.io/mkdocs-material/reference/code-blocks/#highlighting-specific-lines-lines' target='_blank'>Code highlighting</a>  

```js title=""
hl_lines="3-5 11 13" // (1)!
// this will highlight lines 3, 4, 5, 11 and 13
```

1. add this code after the 3 backticks (``` hl_lines="3-5 11 13")

```py title="example with lines 3-5 11 13" linenums="1" hl_lines="3-5 11 13"
# Code block with ``` (3 backticks)
# for line numbering: linenums="1", to highlight lines: hl_lines="3-5 11 13"
mkdocs.yml    # The configuration file.
docs/
   index.md  # The documentation homepage.
   ...       # Other markdown pages, images and other files.
# useful links:
hamk.fi
github.com
# comment
the 11th line is highlighted
# comment
replace the following with your own 'username' and 'password'
```

## In line highlight
!!! info "documentation"
    MkDocs-material <a href='https://squidfunk.github.io/mkdocs-material/reference/code-blocks/#highlighting-inline-code-blocks' target='_blank'>Highlighting inline code blocks</a>  

```yaml title="mkdocs.yml"
markdown_extensions:
  - pymdownx.highlight:
    anchor_linenums: true
  - pymdownx.inlinhilite # in line highlight
  - pymdownx.snipets
```

Examples of inline highlight (inlinehilite):  
1. Here is some code: `#!py3 import pymdownx; pymdownx.__version__`.  
2. The python `#!py range()` function is used to generate a sequence of numbers.  
2b. The python `#!python range()` function is used to generate a sequence of numbers.  
3. The mock shebang will be treated like code here: `#!js var text = 'HAMK';`.  
3b. The mock shebang will be treated like text here: ` #!js var  text = 'HAMK'; `.  
4. Do not expose your `password`.  

## Syntax highlight

!!! info "documentation"
    1. <a href='https://squidfunk.github.io/mkdocs-material/setup/extensions/python-markdown-extensions/?h=syntax+hi#inlinehilite' target='_blank'>MkDocs-material Syntax Highlighting</a>  
    2. details in MkDocs-material <a href='https://squidfunk.github.io/mkdocs-material/setup/extensions/python-markdown-extensions/?h=#highlight' target='_blank'>Python Markdown Extensions Highlight</a>  
    3. A 'solution' <a href='https://github.com/squidfunk/mkdocs-material/issues/138'>work around for php</a>
    4. <a href='https://facelessuser.github.io/pymdown-extensions/extensions/highlight/#syntax-highlighting' target='_blank'>FacelessUser Syntax InlineHilite</a>  
    5. For bash, see the <a href='https://github.com/squidfunk/mkdocs-material/discussions/6504' target='_blank'>discussions/6504</a>  
    6. <a href='https://learn.srlinux.dev/blog/2023/sr-linux-syntax-highlighting-with-pygments/' target='_blank'>SR Linux Syntax Highlighting with Pygments</a>  
    7. Cusomization Pygments with MkDocs-material <a href='https://squidfunk.github.io/mkdocs-material/reference/code-blocks/?h=embedd#custom-syntax-theme'>Custom syntax theme</a>
    

```yaml title="mkdocs.yml"
markdown_extensions:
  - pymdownx.highlight
  - pymdownx.inlinehilite
```

```yaml title="the following is not currently used in this project"
#markdown_extensions:
#  - pymdownx.highlight:
#      anchor_linenums: true
#      line_spans: __span
#      use_pygments: true
#      pygments_lang_class: true
```

##### bash (suboptimal)
Currently bash highlighted but suboptimal  
Start at this <a href='https://github.com/squidfunk/mkdocs-material/discussions/6504' target='_blank'>discussion 6504</a> on bash/sh/shell codeblock syntax highlight 
```bash linenums="1"
# this is bash
wsl --set-default-version 2
wsl --list --verbose

wsl -u root -d Ubuntu-24.04 bash -c "touch /etc/wsl.conf"
wsl -u root -d Ubuntu-24.04 bash -c "echo [boot] >> /etc/wsl.conf" 
wsl -u root -d Ubuntu-24.04 bash -c "echo systemd=true >> /etc/wsl.conf" 
wsl -t Ubuntu-24.04

wsl --export Ubuntu "G:\My Drive\Ubuntu_wsl_backup_24.04.tar"

#!/bin/bash
echo "Today is " `date`
echo -e "\nenter the path to directory"
read the_path
echo -e "\n you path has the following files and folders: "
ls $the_path
```

##### css ✓
```css linenums="1"
/*this is css*/
/*HAMK branding colors*/
.md-header {
    background-color: #003755;
    scrollbar-color: #7300F0;
}

/*this is correct, do not remove it*/

.md-tabs {
    background-color: #7300F0;
}
```

##### html (& js)  ✓
```html linenums="1"
<!-- this is html -->
<!DOCTYPE html>
<html>
<body>
<h1>My First Web Page</h1>
<p id="demo">My First Paragraph</p>
<script>
document.getElementById("demo").innerHTML = 5 + 6;
</script>
</body>
</html>
```

##### java ✓

```java linenums="1"
// this is java
public class Main {
  public static void main(String[] args) {
    System.out.println("Hello World");
  }
}
```

##### js ✓
```js linenums="1"
// this is js
document.getElementById("demo").innerHTML = "Hello JavaScript";
```

##### json ✓

```json
{
"name": "Your Name",
"school": "HAMK"
}
```

##### php (suboptimal)
Currently, php highlighted but required `#!php <?`  
'Solution': <a href='https://github.com/squidfunk/mkdocs-material/issues/138' target='_blank'>work around for php</a>  

```php linenums="1"
// this is php //(1)! //This annotation is not enabled
echo "Hello, world!";
function myMessage() {
  echo "Hello world!";
}
myMessage();

// the same code below
// until <? //(2)! //This annotation is enabled thanks to the php opening tag
echo "Hello, world!";
function myMessage() {
  echo "Hello world!";
}
myMessage();

```

1. (1) This annotation is not enabled
2. (2) The code in lines `#!py 2-6` are not highlighted. The same code, lines `#!py 10-14`, are higlighted thanks to the [short] opening PHP tag `#!php <?`, even commented as in line `#!py 9`. Missing the tag also inactivates the annotation (1) above.

##### powershell ✓
```powershell linenums="1"
# this is powershell
$contentToAdd = @"
[wsl2]
memory=4GB # Limits VM memory in WSL 2 to 4 GB
processors=2 # Makes the WSL 2 VM use two virtual processors
[experimental]
autoMemoryReclaim=true
"@

New-Item $home\.wslconfig
Add-Content $home\.wslconfig $contentToAdd
notepad++ $home\.wslconfig

New-Item -Path 'D:\temp\Test Folder' -ItemType Directory
```

##### python ✓
```py linenums="1"
# this is python
data = 'hello world'
print(data[0])
print(len(data))
print(data)
```

##### sh (suboptimal)
```sh linenums="1"
# this is sh (similar appearance as bash)
wsl --set-default-version 2
wsl --list --verbose

wsl -u root -d Ubuntu-24.04 bash -c "touch /etc/wsl.conf"
wsl -u root -d Ubuntu-24.04 bash -c "echo [boot] >> /etc/wsl.conf" 
wsl -u root -d Ubuntu-24.04 bash -c "echo systemd=true >> /etc/wsl.conf" 
wsl -t Ubuntu-24.04

wsl --export Ubuntu "G:\My Drive\Ubuntu_wsl_backup_24.04.tar"

#!/bin/bash
echo "Today is " `date`
echo -e "\nenter the path to directory"
read the_path
echo -e "\n you path has the following files and folders: "
ls $the_path
```

##### yaml ✓
```yaml
# this is yaml
  language: en
  palette: 
    - scheme: slate # put slate first to make dark mode the default one
      toggle:
        icon: material/toggle-switch
        name: Switch to light mode
        primary: red
        accent: lime
    - scheme: default
      toggle:
        icon: material/toggle-switch-off-outline
        name: Switch to dark mode
        primary: indigo
```

## Code annotation
Each line can host only one annotation.  

!!! info "documentation"
    MkDocs-material <a href='https://squidfunk.github.io/mkdocs-material/reference/code-blocks/#code-annotations' target='_blank'>Code annotation Configuration</a>  
    MkDocs-material <a href='https://squidfunk.github.io/mkdocs-material/reference/code-blocks/#adding-annotations' target='_blank'>Code annotation Usage</a>  

##### bash annotate ✓
```bash linenums="1" hl_lines="3"
# this is bash
wsl --set-default-version 2
wsl --list --verbose # (1)!

wsl -u root -d Ubuntu-24.04 bash -c "touch /etc/wsl.conf"
wsl -u root -d Ubuntu-24.04 bash -c "echo [boot] >> /etc/wsl.conf" 
wsl -u root -d Ubuntu-24.04 bash -c "echo systemd=true >> /etc/wsl.conf" 
wsl -t Ubuntu-24.04

wsl --export Ubuntu "G:\My Drive\Ubuntu_wsl_backup_24.04.tar"

#!/bin/bash
echo "Today is " `date`
echo -e "\nenter the path to directory"
read the_path
echo -e "\n you path has the following files and folders: "
ls $the_path
```

1. this should be more colorful

##### css annotate ✓

```css linenums="1" hl_lines="4"
/*this is css*/
/*HAMK branding colors*/
.md-header {
    background-color: #003755; /* (1)! */
    scrollbar-color: #7300F0;
}

/*this is correct, do not remove it*/

.md-tabs {
    background-color: #7300F0;
}
```

1. this is the background color

##### html (& js) annotate ✓
```html linenums="1" hl_lines="5 8"
<!-- this is html -->
<!DOCTYPE html>
<html>
<body>
<h1>My First Web Page</h1> <!-- (1)! -->
<p id="demo">My First Paragraph</p>
<script>
document.getElementById("demo").innerHTML = 5 + 6; // (2)
</script>
</body>
</html>
```

1. including a h1 element to improve SEO
2. script

##### java annotate ✓

```java linenums="1"  hl_lines="4"
// this is java
public class Main {
  public static void main(String[] args) {
    System.out.println("Hello World"); // (1)!
  }
}
```

1.  testing the annotation

##### js annotate ✓
```js linenums="1"  hl_lines="2"
// this is js
document.getElementById("demo").innerHTML = "Hello JavaScript"; // (1)!
```

1. testing the annotation for js

##### json annotate ✓

```json
{
"name": "Your Name", /*(1)!*/
"school": "HAMK"
}
```

1. Replace with your name

##### php annotate ✓
Currently, php highlighted but required the opening PHP tag <?php  
'Solution': <a href='https://github.com/squidfunk/mkdocs-material/issues/138'>work around for php</a>  

```php linenums="1" hl_lines="10"
// this is php
echo "Hello, world!";
/* not highlighted until leaded by the opening PHP tag, even commented, as shown right below */
function myMessage() {
  echo "Hello world!";
}
myMessage();

// until <?php
echo "Hello, world!"; // (1)!
// this is php
function myMessage() {
  echo "Hello world!";
}
myMessage();
```

1. echo to print to console

##### powershell annotate ✓
```powershell linenums="1" hl_lines="10"
# this is powershell
$contentToAdd = @"
[wsl2]
memory=4GB # Limits VM memory in WSL 2 to 4 GB
processors=2 # Makes the WSL 2 VM use two virtual processors
[experimental]
autoMemoryReclaim=true
"@

New-Item $home\.wslconfig # (1)!
Add-Content $home\.wslconfig $contentToAdd
notepad++ $home\.wslconfig

New-Item -Path 'D:\temp\Test Folder' -ItemType Directory
```

1. Adding new item

##### python annotate ✓
```py linenums="1" hl_lines="3"
# this is python
data = 'hello world'
print(data[0]) # (1)!
print(len(data))
print(data)
```

1. The python print() is to print to terminal

##### sh annotate ✓
```sh linenums="1" hl_lines="14"
# this is sh (similar appearance as bash)
wsl --set-default-version 2
wsl --list --verbose

wsl -u root -d Ubuntu-24.04 bash -c "touch /etc/wsl.conf"
wsl -u root -d Ubuntu-24.04 bash -c "echo [boot] >> /etc/wsl.conf" 
wsl -u root -d Ubuntu-24.04 bash -c "echo systemd=true >> /etc/wsl.conf" 
wsl -t Ubuntu-24.04

wsl --export Ubuntu "G:\My Drive\Ubuntu_wsl_backup_24.04.tar"

#!/bin/bash
echo "Today is " `date`
echo -e "\nenter the path to directory" # (1)!
read the_path
echo -e "\n you path has the following files and folders: "
ls $the_path
```

1. \n to go to next line and print the content after \n (in this example, "enter the path to directory" will be printed in the next line)

##### yaml annotate ✓
```yaml linenums="1" hl_lines="4"
# this is yaml
theme:
  features:
    - content.code.annotate # (1)!
```

1. I'm a code annotation for yaml! I can contain `code`, __formatted
    text__, images, ... basically anything that can be written in Markdown.
