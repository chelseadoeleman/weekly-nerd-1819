# BEM (Block, Element, Modifier)

Writing CSS is first all fun and games, but after a while you can get lost in your own code. Sometimes you write a ton of code lines in one file and can't see the wood for the trees, which results in not wanting to touch the code ever again. Afraid you might change a lot more than you bargained for due to specificity and cascading. Luckily there a lot of CSS methodologies that help you organize your CSS so your or the next person that touches your CSS doesn't have to wreck their brain over you code.

## What is BEM?

**BEM** stands for **Block, Element, Modifier** and is an CSS methodology like, **SMACSS** (Scalable and Modular Architecture for CSS), **OOCS** (Object Oriented CSS), **ACSS** (Atomic CSS), **SUITCSS**(Style tools for UI components) and **oCSS** (organic cascade style sheet). CSS methodology help you organize your code, maintain your codebase and making sure everyone 'speaks the same language' when talking about different components/elements in a webpage. CSS methodologies are extremely useful when you have a big project with a large codebase and you have to pass code through to others. Because when someone understands a methodology that has been used, everybody knows what they're talking about and thus makes it easier to maintain. 

### So what does Block, Element, Modifier mean?

So the **block** element is a standalone entity like an ```<input />``` for example. The **element** for an ```<input />``` can be a ```<label />```, which is semantically tied to a **block**. We all know a input needs to have a label for a good user experience and accessibility. And lastly we have a **modifier** this is added to create a certain specific appearance for that **block**.

```html
<label class='input__label'>
    Name
    <input class='input input--big input--small' type='text'/>
</label>
```
In CSS you are able to target them as follows:

* Block: ```.input { }```
* Element: ```.input__label { }``` specified by two lowerdashes __ between a block and a element.
* Modifier: ```.input--big{ }``` or ```.input--small { }``` specified by two dashes -- between a block and a modifier.

## Why use BEM?

Seems like a whole lot of trouble to go through when setting up a project, specifying each element with a classname. But in the end it will save you a whole lot of trouble

**specificity**

## BEM in SASS