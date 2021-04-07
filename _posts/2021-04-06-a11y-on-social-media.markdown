---
layout: post
title:  "Accessibility on Social Media"
date:   2021-04-06 23:49:52 +0100
categories: posts/a11y
author: Marvin Borisch
---
**Tech-knowledge needed:** basically none

*Hey friends, every **five seconds** a human goes blind on planet earth. In fact, while you have read this sentence, another human has gone blind already. I have noticed that a lot of developers and website owners are not aware of how many people try to visit their websites and apps without the ability to even see the content. While this problem has been pushed more into the spotlight since laws have been passed around the world in the recent years, many people forget to apply that knowledge onto their social media accounts. As some of you know, this topic is a pretty important one to me for multiple reasons.*

*The main reason might be, that a good friend of mine was raised by a blind single mother. She has raised four children, all by herself. Now imagine how pissed you would be after a long day of taking care of your kids all by yourself and just wanting to check out what your friends are doing on social media but can not participate. That's why I am writing this article. I hope everyone of you will gain some sensitivity to disabilities and how they affect the online-life of around 37.000.000[^1] humans world wide.*

### Explanation
In this article I will focus on Twitter, but all big players on the social media market have similar functions. Feel free to ask me on a Twitter DM or give me a call if you need help finding the functions on other plattforms. The information I am providing here, even though they are based on Twitter, will give you a basic understanding on how to improve the online quality for your friends and followers with disabillities in general.

### Viewing Disabillity
Humans with viewing disabilities such as blindness, reduced view, contrast problems, color blindness and everything else I am not covering here, have a hard time getting informations out of your images and photos. You can cover most of their problems with two easy tricks.

#### ALT-tag / Description

The "ALT"-tag, or how twitter calls it "Description", of a photo is a hidden text that can be read by machines. While a lot of shady and dsigusting professional content creators abuse the function to push theirself further up on Google, it actually has a useful function. Blind people use so called **screen readers**. That can be a installable service that reads the text for you or even a machine that translates the displayed text into braile[^2]. Without such ALT-tags, blind people won't be able to consume your photos. So here is how to describe the photos to blind people. <span class="notes">The following example is for tweets, but you can add a ALT-description to "Fleets", too.</span>

![Twitter Upload-mask with a "Add Description" link below the photo.][01-upload]<br>
*[open image][01-upload]{:target="_blank"}*{:class="imglink"}<br>
When you upload a photo to twitter, you can spot the little "Add Description" function below it. If you click that link, you will be prompted with a information from Twitter.

> You can add a description, sometimes called alt-text, to your photos so they're accessible to even more people, including those who are blind or visually impaired. Good descriptions are concise, but present what's in your photos accurately enough to understand their context.

After closing that prompt from twitter, you can start describing the photo. Keep it compact but descriptive. On twitter you have 1.000 characters to describe your photo. If you feel you have described the picture good enough, hit the save button. If you have done everything correctly, you will see a "ALT" label on the left bottom corner and the excerpt of your description below of your photo preview. Finish your tweet and tweet it out to the world.

![The ALT-label is now showing on the left bottom corner of the photo preview.][04-final-check]<br>
*[open image][04-final-check]{:target="_blank"}*{:class="imglink"}<br>

For all the (upcoming) nerds of you, I have [a screenshot][06-code]{:target="_blank"} of how the ALT tag will be inserted into twitters website. This is basically what screen readers will see. To check it yourself, right-click your photo and then hit "inspect" (or similar, based on your browser). This will open a window with a lot of eeky weeky code stuff and highlight the important shit.

Now you are ready to go. With that information, you can now describe your photos to everyone and, kind of, do some magic by making the blind "see" your photos. They will thank you, not by words, but by their hearts.

<span class="notes">**Note:** Of course no one should feel obligated to add ALT-descriptions, it is a nice-to-have. But if you are a public figure, represent your enterprise, company, or some official position, you should consider adding ALT-descriptions for the sake of inclusion.</span>

#### Contrasts
The biggest mistake most designer do, even good ones, is forgetting to check the contrast ratio. While working with a lot of them in my career, I've learned that contrasts are way to underrated, even though they impact a way bigger amount of humans. And I am not only talking about visually impaired people. Bad contrasts can affect even you. Take my website for example. I have designed my website purely for me and no one else, that means I have used my main monitor[^3] as the basic display instead of testing my design on multiple monitors. The contrast itself is perfectly fine on my main monitor, but if I use my secondary monitor, I have to focus much more to read my <span class="notes">article notes</span>.

![An example of different color contrasts based on my website design][07-contrast]<br>
*[open image][07-contrast]{:target="_blank"}*{:class="imglink"}<br>

Problems might occur due to a mix of size, weight (thickness) and the colors of the foreground and the background. That's why some very clever people have agreed on principles for inclusive design[^4], but I do not expect you to read through all this. You can simply visit [contrastchecker.com](https://contrastchecker.com/){:target="_blank"} and test if your colors meet the standards. But do not rely to much on it. Sometimes contrasts can appear better and sometimes worse than calculated. For example, yellow/orange and white **can** look like it is functioning for you, but based on the light source, it can turn bad really fast. On the other hand a medium-grey on a true black background might not fit all of the calculations for the AA/AAA standard, but is readable for a wide amount of humans in most light situations.

***"So, Marv, how can I optimize my social media contrast game?"***, you migh ask. It's pretty easy. Choose good color and hue contrast, and if you want to put some text on a nice photo of yours, make sure to either use a background behind the text or put it on a part of your image, that has a quite opposite color or hue. Always ask yourself "could my grandparents read it?". Are you not sure if the answer is yes? Then the answer most likely will be "no". One easy quick-tip that helps me a lot is, taking my phone in my hand, and move it as far away from my eyes as my arms reach. If you still can read everything without guesstimating, then you are ready to go.


### Hearing Disabillity & Audio Language Barriers
Based on statistics provided by the WHO[^5], over 5% of the world's population require rehabilitation because of their disabling hearing loss. That's over 430.000.000 humans. Yet a lot of social media content does not provide support for disabled people. Sadly, there aren't many solutions on how to aid deaf, partially restricted and foreign humans. But available solutions are very powerful and surprisingly including.

#### Manual Subtitles
The easiest way to include humans with hearing disabilities is to add subtitles. Most plattforms, including Twitter, do not deliver platform-ready solutions for that. You are mostly restricted to manually add subtitles with third-party programms. As there are thousands of awesome and free to use programms, I will not recommend any specific ones, but a easy and quick online search for terms such as "(permanently) add subtitles on video" will throw out quite a handfull of awesome tools. Make sure to consider my tipps for contrasts as mentioned above.

#### Youtube Subtitles
While most social media plattforms do not support subtitles in their standard functions, Youtube basically ~~is~~ was the queen of subtitles. Due to Youtube's nature of providing video content to billions of humans world wide, they've almost perfectioned the subtitle game. They offer functions such as manually adding subtitles to your videos which can be shown and hidden, based on the user's preference. But the most important functions might be auto-generated synchronization, auto-generated translations ~~and community-submitted subtitles~~.

**Auto-generated Synchronization:** If you provide a full transcript of the video, Youtube's system will automatically place the timing-markes for you. No need to do all the handy work on your own.

**Auto-generated Translation:** When you add subtitles by yourself, Youtube can automatically translate your video in any supported language. Tho, this function does not work for auto-generated syncronizations, it is still a very handy function.

**Legacy: Community-submitted Subtitles:** In the beginning of the world wide Covid-19 pandemic, Youtube decided[^6] to remove it's function of community captions. As they have stated, this decision was made due to low usage and spam/abuse problems. Sadly, Youtube has not announced any replacement of this function. The a11y-community of Youtube has been suggesting replacements such as volunteer-created captions, which would have been a huge support for disabled content creators. It is little surprise that this sparked a backlash from the community.

>I told them for a full freakin' hour why we need community contribution. Not just for deaf people so more channels will have captions, but for disabled creators who can't manually do them or have the income to pay for them: which is most of us. They do not care about us.<br><br>
>¬ <cite> Rikki Poynter (<a href="https://twitter.com/rikkipoynter/status/1289004897371856898" target="_blank">@rikkipoynter</a>), July 31, 2020</cite>

Even though this sad downside, Youtube still offers good subtitle options for content creators, which will still help a lot of people to provide more accessible content for disabled or impaired humans. Due to it's almost fully automatic nature, there is no reason **not** to provide subtitles for your friends and followers.

### It's about you! Help.
You will never know if you will ever be impacted by a disability in your future or if your friends and family will strugle from poor a11y-support, so it is about you to make this world a better place by supporting your fellow humans.

If you think I have been mistaken, forgotten a vital part or if you got some valuable insight to share, feel free to contact me via Twitter. I will be happily open to extend this post.



<hr>
<span class="notes">Footnotes</span>

[^1]: 37.000.000 humans world wide, that would be roughhhhly half the amount of the inhabitants in germany! Around 145.000 people in germany are fully blind. That's more than half of the inhabitants of my district, Berlin Treptow-Köpenick.
[^2]: Check out this video about a refreshable braille display for the iPad. [YouTube Link](https://www.youtube.com/watch?v=tVuLGrab9JA){:target="_blank"}
[^3]: As my main monitor I use a EIZO EV2336W, a monitor made for office works and designer with a modern and bright but economical background lighting. My secondary monitor is a old HP Compaq LA1951g in vertical mode with bad background lighting.
[^4]: WCAG Contrast Minimum, by W3C. [Read here](https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum.html){:target="_blank"}
[^5]: World Health Organization: Deafness and hearing loss. [Read the full article](https://www.who.int/news-room/fact-sheets/detail/deafness-and-hearing-loss){:target="_blank"}
[^6]: Youtube about removing community captions. [Read on Youtube Support](https://support.google.com/youtube/answer/6052538?hl){:target="_blank"}


[01-upload]: /pictures/a11y-on-social-media/01-upload.jpg "Upload Mask"
[04-final-check]: /pictures/a11y-on-social-media/04-final-check.jpg "Upload Mask with Description"
[06-code]: /pictures/a11y-on-social-media/06-code.jpg "Code preview"
[07-contrast]: /pictures/a11y-on-social-media/07-contrast.jpg "Contrast examples"