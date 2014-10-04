Menu Alert
=========

In this project you'll be able to parse a menu for presence of a certain item.

We will be making an alert for the particular item in mind, you will get to choose the restaurant and menu item/ingredient.


## Creating the script

A step by step description of creating the script is below:

### Wget

`wget` can get the blueprint -- or source code -- of any website. This blueprint will 99% of the time contain all the information presented in the website.


use 

`wget https://www.google.com/` to get the source of google's search engine


to save the output a particular filename (example, `some_site.html` use :

`wget -O "some_site.html" https://www.google.com/`

and your output will be saved into `some_site.html` in the directory you were in when you typed `wget`.

Go head and try that on your site, and save the file to a unique name.

My example, looking at pizza options for tonight, I like the name `pizza_options.html`:

`wget -O pizza_options.html http://newyorkpizza.biz/menu/specialty-pizzas/`


### Grep

Let's find out every line which has the word we're looking for in it, in my case, I'm looking for garlic:

`grep "garlic" "pizza_options.html"`

(if you want to have the actual match highlighted use: `grep --color "garlic" "pizza_options.html"`)

oops noticing below we're getting stuff from the meta tag, let's get rid of that result:

```html
<meta property="og:description" content="Salami, pepperoni, ham, mushrooms, olives, bell peppers &amp; Italian sausage. Mushrooms, olives, bell peppers, onions, tomato &amp; fresh garlic. Chicken ..." />
<h5>Mushrooms, olives, bell peppers, onions, tomato &#038; fresh garlic.</h5>
<h5>Chicken breast, mushrooms, onions, bell pepper &#038; garlic.</h5>
<h5>Bay shrimp, sun-dried tomato, mushrooms, onions, garlic &#038; fresh basil pesto sauce.</h5>
```

REGEX TO THE RESCUE!

we only want certain lines, let's look for a pattern. Non-meta lines, all begin with an `<h5>` tag, so let's limit our results to this.

The problem is that there's going to be unknown letters between `<h5>` and `garlic`, we'll use the handy combo `.*`:

`grep "<h5>.*garlic" "pizza_options.html"`

`.*` preserves the match even if there are characters between `<h5>` and `garlic`.

now our results are all good:

```html
<h5>Mushrooms, olives, bell peppers, onions, tomato &#038; fresh garlic.</h5>
<h5>Chicken breast, mushrooms, onions, bell pepper &#038; garlic.</h5>
<h5>Bay shrimp, sun-dried tomato, mushrooms, onions, garlic &#038; fresh basil pesto sauce.</h5>
```

### Counting with Grep

We can easily count the number of pizzas with garlic by using the `-c` option:

`grep -c "<h5>.*grep" "pizza_options.html"`

At the time of writing this gives me `9` pizzas total.


### Git 


### Bash


### Crontab



## Stuff we'll cover


Stuff you'll learn to use:
* [ ] wget
* [ ] grep
* [ ] git 
* [ ] crontab (scheduling)

Topics/skills we'll cover:
* [ ] piping
* [ ] regex
* [ ] and bash scripting
