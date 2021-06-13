---
layout: post
title:  "Sustainable Design Thinking in Webdevelopment"
date:   2021-06-13 17:17:17 +0100
categories: posts/susty
author: Marvin Borisch
---
**Tech-knowledge needed:** basic

*In 2020 the carbon dioxide emissions of the world has raised to shocking 39.9 billion tons by year. Digital technologies account for 4% of the greenhouse gas emissions. That number is scaringly high, but we, the developers of this digital world, can do something against it by changing our design mindset. Here are a few ideas on how to approach this topic.*

*Be warned, this article is highly theoretical and was written to inspire you, not to lecture you on how to design. Tho, this article is part of my 2021 focus interest **Maximum sustainability design-extremism**. Here are some takes on how to design with sustainibility extremism in your mind. As I am a tech-lead with a webdesign and &#8209;developing background, let me show you a few web examples.*

### Design useful not stylish
Don't get me wrong, I do not want you to design ugly websites, systems or apps, but one of the most impactful ways to approach a cleaner internet is to design for the use and not for the style. The thumbrule I've soaked into my design process is **"does the user gain information from this effect?"**. You'd be surprised how often this question can be easily answered with **no**. 

#### Javascript effects
The biggest but also easiest to avoid impact is to reduce the extreme use of javascript effects. Reducing javascript effects does not only reduce the carbon footprint of your project, but it also reduces the chances of you, the designer, distracting your users from actually getting valuable information.

Swaying waves, moving textblocks and flashing images might look "cool" and "modern", but they do not only distract the user but also come with multiple costs.

**The Code and it's impact on you and the user**<br>
The code itself has a "weight" which we express as bytes. Every byte costs us CO2. It starts with the time we spend to write such effects, which results in longer computing and sitting-infront-of-the-computer time. That costs electricity for the computer, the monitor and also for ourselves. The CPUs of our computer and even of our body need to be "feed" energy. We can apply Einstein's Mass–energy equivalence here. Everytime we hit a key on our keyboard, we burn energy. We think about what we code and our fingers execute that produced idea. The code itself is written on a computer. Each key stroke costs energy. Every file uses storage which is written, rewritten and read within miliseconds, writing and reading our hard-drives costs energy. And we aren't even done yet. Saving these javascript files towards our host, you get it, costs energy. Running the host costs energy. When a user visits the website for the first time, transfering the data will cost energy. Executing the effect that has been written into the javascript uses the users CPU[^1], RAM and sometimes even the GPU and therefore: costs energy.

Wavy backgrounds animated in javascript (yes, and CSS, too) are processed every single time the state changes. So if you have a loop of a effect instead of an effect that only fires one time, you are forcing the user to waste energy as long as the user visits the website. You can check that in your DevTools in the **Performance Monitor** tool. I've used the (beautiful) website of Asana for example. They fire floating labels over the hero image via javascript, that float and float and float without ever stopping. Each frame of the effect is processing information and therefore using the users CPU which results in usage of energy.

![The Devtools "Performance Monitor" on Asana's landingpage][01-cpu-and-recalc]<br>
*[open image][01-cpu-and-recalc]{:target="_blank"}*{:class="imglink"}<br>

You might think I am counting peanuts here, and I might am, but there are milions of websites with a unimaginable amount of javascript effects that have no use at all. If you combine every miliseconds that are processed by useless effects, you will end up having a huge carbon footprint. If every designer would ask themself "does the user gain information from this effect?" more often and act accordingly, we could reduce carbon footprint globally. And this is just one measurement you can implement into your design thinking process. After two or three projects, you will act more responsible by default. 

**Awesome sideffect**<br>
Using less useless javascript effects would not only result in lesser energy usage but also loads the website faster, it saves miliseconds of loading time and therefore also saves energy. You have a win-win-win situation here: You give the user a faster web experience and contribute to saving the enviroment by using less energy for the transfer of the files and save time coding that effect which results in faster delivery for your client and less needed energy of your body. And if you care about money, then it's also a additional sideffect: you spend less money.

### Pinpoint redundancy, eradicate repeats
One of the things most beginners and even some professionals do wrong is repeating stuff. I myself am a victim of lazyness and therefore sometimes include redundancy in projects. The biggest problem is the idea of "Ahh, no worries, I can fix that later!". Based on my 10+ years of professional experience I can tell you that in most cases you will **not** have the time to fix things later on, as long as a client doesn't see the need of the fix. It is about you to include that into your design thinking process. Here are two examples on my biggest mistakes.

#### Reusable code in Wordpress
*As over 50% of my projects are based on wordpress websites for SME, I am using this example. This can be replaced with most traditional CMS, headless CMS and modern package-based development styles.*

Most websites have code snippets that are most likely to be re-used in the code design. This starts with wordpress' own head and footer calls but doesn't end there. Template parts[^2] are a good example for re-usable code but are, based on my insight, mostly only used for loops. These template parts can also be used for repeatable code such as api-based forms, promotional sections and basically everything you use more than just once.

The biggest complaint I've heard from beginners or front-end developers is, that reusable code isn't very flexible. While this might was true a few years ago, todays technology can help you with that. By designing your front-end with CSS Grid or Flexbox-Grids, you can re-arrange the content of the re-used code's DOM as simple as 1234.

#### Reusable CSS or SCSS/LESS
The biggest problem in front-end design **was** re-using styling, as example, you had to re-define shadows for cards every single time you wanted to declare them. With the introduction of LESS and SCSS, reusable styling was introduced. While most beginners only use the variables to set colors, fonts or sizes, the actual gamechanger are so called *Mixins*[^3]. You can set multiple lines in mixins and reuse these lines in the styling process. This may not reduce the lines of css for the visitor of the project, but it reduces the lines you have to write and therefore reduces your usage of energy as mentioned in **Javascript effects** above.

**Example:**<br>
![The declaration of a Mixin in SCSS][02-shadow]<br>
*[open image][02-shadow]{:target="_blank"}*{:class="imglink"}<br>
![Usage of the declared Mixin][03-card]<br>
*[open image][03-card]{:target="_blank"}*{:class="imglink"}<br>

You can check out the example [on codepen](https://codepen.io/marvinpoo/pen/rNyQjeX){:target="_blank"} . Mixins can technically be used for everything even though I would suggest using it for multi-line styling. It doesn't have to be complex at all, but you can even create awesome mobile first responsive/fluid declarations as you can see at my (very old) [_marvli](https://github.com/marvinpoo/_marvli.scss){:target="_blank"} preset.

### Conclusion
These are just some examples that would reduce your carbon footprint of your projects. It is about you to ask yourself: is it needed? Is it redundant? If we all absorb critical thinking about the usage of our code, we could reduce the impact on our environment, optimize the usage of recources and also save a lot of time and money.

We only have this one planet for now and therefore have to respect our home and it's resources. It is easy and mostly comes with a lot of benefits. Now it is time for us to act accordingly. Together as humans we can solve human problems. After all we are one species.

<hr>
<span class="notes">Footnotes</span>

[^1]: Learn more about CPU usage of Javascript animations [on Javascript Info](https://javascript.info/js-animation){:target="_blank"}.
[^2]: Code Reference of Template Parts [on Wordpress Dev Docs](https://developer.wordpress.org/reference/functions/get_template_part/){:target="_blank"}.
[^3]: Mixin and Include documentation [for SCSS/SASS](https://sass-lang.com/documentation/at-rules/mixin){:target="_blank"}.

[01-cpu-and-recalc]: /pictures/sustainable-design-thinking/01-cpu-and-recalc.jpg "Devtools Performance Monitor"
[02-shadow]: /pictures/sustainable-design-thinking/02-shadow.jpg "Shadow Mixin"
[03-card]: /pictures/sustainable-design-thinking/03-card.jpg "Usage of Mixin"