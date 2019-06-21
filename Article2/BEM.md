# BEM (Block, Element, Modifier)

Writing CSS is first all fun and games, but after a while you can get lost in your own code. Sometimes you write a ton of code lines in one file and can't see the wood for the trees, which results in not wanting to touch the code ever again. Afraid you might change a lot more than you bargained for due to specificity and cascading. Luckily there are a lot of CSS methodologies that help you organize your CSS so your or the next person that touches your CSS doesn't have to wreck their brain over you code.

## What is BEM?

**BEM** stands for **Block, Element, Modifier** and is an CSS methodology like, **SMACSS** (Scalable and Modular Architecture for CSS), **OOCS** (Object Oriented CSS), **ACSS** (Atomic CSS), **SUITCSS**(Style tools for UI components) and **oCSS** (organic cascade style sheet). CSS methodology help you organize your code, maintain your codebase and making sure everyone 'speaks the same language' when talking about different components/elements in a webpage. CSS methodologies are extremely useful when you have a big project with a large codebase and you have to pass code through to others. Because when someone understands a methodology that has been used, everybody knows what they're talking about and thus makes it easier to maintain. 

### So what does Block, Element, Modifier mean?

So the **block** element is a standalone entity like an ```<input />``` for example. The **element** for an ```<input />``` can be a ```<label />```, which is semantically tied to a **block**. We all know an input needs to have a label for a good user experience and accessibility. And lastly we have a **modifier** this is added to create a certain specific appearance for that **block**.

```html
<label class='input__label'>
    Name
    <input class='input input--big input--small' type='text'/>
</label>
```
In CSS you are able to target them as follows:

* Block: ```.input { }```
* Element: ```.input__label { }``` specified by two lower-dashes __ between a block and an element.
* Modifier: ```.input--big{ }``` or ```.input--small { }``` specified by two dashes -- between a block and a modifier.

## Why use BEM?

Seems like a whole lot of trouble to go through when setting up a project, providing each element with a classname. But in the end it will save you a whole lot of trouble. 

Using BEM will save you a lot time writing double code, because you already provided the blocks with modifiers it's easier to oversee which styles you already implemented. So when you need a certain element do a something you might already have a modifier defined that exactly does that kind of thing.

It's also easier to see which element is connected to the other, thus depending on the other. Because you can see which element is tied to a block. This makes the structure understandable for everyone for none developers. This way you create some sort of language that everybody understands, thus changes can easily be discussed with other parties involved in the project.

### Specificity

> **"If you have two (or more) conflicting CSS rules that point to the same element, there are some basic rules that a browser follows to determine which one is most specific and therefore wins out."** - Patrick Griffiths

```css
.btn {
    background-color: blue;
    background-color: red;
}
```

When giving a button a ```background-color: blue;``` and on that same button you provide another ```background-color: red;``` beneath the blue one, your button will turn up red. This is because of cascading in CSS. 

```css
.form .btn {
    background-color: blue;
}

.btn {
    background-color: red;
}
```

But when writing it like so the former will be used, because it is more specific, turning your button blue.
When you have a lot of CSS and don't have a grip on all the specificity you can change something in the file and it won't work, because somewhere there is something more specific overwriting that line of code. Which can take ages to figure out where to start and after you will likely run into the same problem again.
For more information about specificity check out this [article](https://stuffandnonsense.co.uk/archives/css_specificity_wars.html) or check out this image from there below:

![Specificity wars](./assets/specificity.png)

Because everything in BEM is a class it creates a very flat structure, where there is almost no conflict with specificity. Resulting in more confidence to work on the project, because you will where to change stuff and what will happen when you change it.

**!NOTE: Nested selectors are not BEM**  

With BEM there is nothing nested so the following is not applicable to BEM.

```css
.form .input-big {
  background-color: white;
  padding: 2rem;
}
```
Writing you CSS like so will create problems with specificity again, which is one of the benefits of BEM because it doesn't almost has any problems with specificity. So keep in mind that you don't want block styles overwriting other block styles. 

## BEM in SASS

[SASS](https://sass-lang.com/guide) is a CSS preprocessor meaning it will generate your CSS following a certain syntax, to create more structure and make it easier to maintain. 
SASS is a preprocessor that is pretty big in the industry right now. Looking back at the CSS of our first component it will probably look something like so in your CSS:

```scss

.input {
    font-size: 1rem;

    &__label {
        color: red;
    }

    &--big {
        padding: 2rem;
    }

    &--small {
        padding: .5rem;
    }
}


```

Because of the dashes and syntax highlighting, it's easy to differentiate between modifiers and elements. Things can get tricky though when defining ```&--big``` scoped into ```__label```, because ```.input__label--big``` does not exist. So be aware of which scope you are working in! To keep nesting you can use ```$self``` in your component like so, this will define it's scope.

```scss
    .input {
        $self: &;
    }
```
Here you can find more information on that [topic](https://css-tricks.com/using-sass-control-scope-bem-naming/).

## Would I use BEM?

I worked with SMACSS before and to be honest at first I was totally lost. I actually got the feeling I was writing more CSS instead of writing less, which didn't feel quite right to me. I also tended to forget to add a classname to an element, because time was of the essence. So writing classnames for every element will sure take some time getting used to, but I think in the long run writing CSS following a CSS methodology, it being SMACSS or BEM, has a lot of benefits. 

My preference goes out to BEM at the moment, because of its structure and integration with SASS. Which makes the structure of a certain component really understandable to me. With SMACSS you would still have different components in different css files, resulting in constantly having to switch between CSS files to get something done. 

## Conclusion

* With BEM you are able to 're-use' modifiers, so you don't have to write double code.
* It creates a certain structure that makes your code a lot more readable and understandable.
* There is almost no specificity with BEM, because everything is a class and nothing is nested.
* Using BEM is still a choice and will definitely not solve all your problem, but can solve a few of them!

## Resources

* [BEM 101](https://css-tricks.com/bem-101/)
* [BEM](http://getbem.com/introduction/)
* [Methodologies](https://github.com/ikkou/awesome-css#architecture)
* [Specificity wars](https://stuffandnonsense.co.uk/archives/css_specificity_wars.html)
* [Specificity](https://www.htmldog.com/guides/css/intermediate/specificity/)
* [Scopes in with SASS](https://css-tricks.com/using-sass-control-scope-bem-naming/)
* [CSS Preprocessor](https://developer.mozilla.org/en-US/docs/Glossary/CSS_preprocessor)
* [SASS](https://sass-lang.com/guide)

