---
title: 'Creating my website with Hugo'
summary: 'I will explain my reasons for having a blog and a personal website. I will illustrate the preceding decision process for choosing the appropriate technologies. I decided to go with the static site generator Hugo. It is a text file based Content Management System (CMS). I also compared Jekyll to Hugo. I will show some features of Hugo, like support for themes, syntax highlighting, and support for typesetting Math/LaTeX expressions in HTML sites. Finally, I will share my experiences so far with the technology.'
tags: [HUGO, Academic, static site generator, CMS]
math: true
slug: creating-my-website-with-hugo
date: 2018-05-17T8:35:00+02:00
lastmod: 2022-02-22T16:28:14+01:00

image:
  caption: 'Isle of Skye 🏴󠁧󠁢󠁳󠁣󠁴󠁿'
---


#### Why??

For some time I've had a strange need for a personal website, though I didn't even know what content to share. The idea of having a blog felt a bit weird
to me, as I was wondering for whom this might be meaningful. It took me a while, but meanwhile I think completely differently about this.

1. You do not have to write long papers that meet academic requirements. Small things can matter, and also imperfect ones. Admittedly far from being imperfect,
   Adam Bien's [Blog](http://adambien.blog/roller/abien/) posts are always succinct and usually provide elegant and low complexity solutions to very concrete
   problems. It's especially because of this brevity that they are easily consumable and very worth reading. Having the infrastructure already set up lowers the
   hurdles to publish even small content.

2. Other people and companies can gain insight into your interests and current projects. This can also be helpful to get in touch.

3. You do not know if you have fully understood a certain topic until you have explained it to someone or have written it down. In turn when blogging you
   ensure a proper understanding.

And at least with every blog post I will get some more practice with my English skills. :us:


#### How?

While doing a first bit of web research for appropriate technologies it seemed that [WordPress](https://wordpress.org/) is the most popular system for websites
with blogs. However, I couldn't bring myself to accept the downsides. Under no circumstances I wanted to host the system myself. Even though there are
countless WordPress hosting providers you either have annoying limitations like ads on your site or a regular downtime. Or you have to pay for the service.
Besides that WordPress felt like a complex and feature-blown system that is hard to tame, especially if you are relying on the installation of your hosting
provider and cannot _just apply a change_. Migrating WordPress sites from one provider to another seems to be easily manageable by export/import functionality.
Nevertheless, you still have some kind of vendor lock-in for your precious content.

Inspired by Trisha Gee's blog post [Converting Blogger to Markdown](https://trishagee.github.io/project/atom-to-hugo/) I came across text file based
generators for static websites with basic Content Management Features. It's the perfect fit! I can write the content in simple text files, e.g. in Markdown
syntax. Definitely no vendor lock-in! And I can easily put them into a version control system.
I use a GitHub [repository](https://github.com/stefanneuhaus/stefanneuhaus.org) for this. As I also have the local copy of the repository on my machine I
feel sufficiently safe and even resign an additional backup. It takes a mere run of the generator to get the readily deployable website in the output
directory. Upload this directory to the web hosting provider of your choice and you're done. I chose [GitHub Pages](https://pages.github.com/), simply
because it's free, I already have a GitHub account, and I like the deployment process of just doing a git commit/push to
my [repository](https://github.com/stefanneuhaus/stefanneuhaus.github.io).


#### Jekyll or Hugo?

The two currently most popular static site generators are [Jekyll](https://jekyllrb.com/) and [Hugo](https://gohugo.io/), at which I had a closer look. I took
the following factors into account:

* Still being actively developed and maintained?
* Documentation
* Programming language, installation, and dependencies
* Performance
* Writing/development workflow
* Built-in features
* Extensibility and flexibility
* Theme support
* Syntax highlighting for code samples
* Support for mathematical notation in content

There is a recently published and very nice comparison by Chris Macrae, which I used as a starting point:
[Hugo or Jekyll? 6 Factors You Should Know](https://forestry.io/blog/hugo-and-jekyll-compared/). As my requirements are fairly low and both options are
battle-tried mature tools, it is clear that either of them would definitely meet my requirements. Nevertheless, I did a comparison.

Soon a tendency towards Hugo became apparent. Although my site is just a tiny one I cannot make a secret of the fact, that performance was one reason. And
this is where Hugo beats the pants off Jekyll. I also liked the ease of installation, as Hugo is written in Go and comes as a self-contained binary. This
seemed easier than fiddling around with the Ruby Gems of Jekyll. I have not been intimidated by the reputed steeper learning curve of Hugo's template syntax
but rather appreciated the rich feature set. This is purely subjective of course.


#### Layout

So I gave Hugo a try. First I had to decide if I wanted to write all layout templates from scratch or pick one of the numerous available
[themes](https://themes.gohugo.io/). As I want to concentrate on the content and do not like to re-invent the wheel, I decided to use a theme as a basis.
Besides that I am no UI/UX expert and it probably would take me a lot of time to come up with an appealing result. I did not agonize about this decision for
a long time: If I do not like my current theme anymore, switching themes should be a piece of cake.

As a theme I chose [Academic](https://sourcethemes.com/academic/), mainly because of its clean design and as it is still being actively maintained. As a plus it
ships with a couple of nice widgets that you can integrate into your site.

_Using_ a theme is done by copying it to the `themes/` directory and enabling it in the site config file. I did not just _copy_ the theme, but added a fork of
the theme [repository](https://github.com/gcushen/hugo-academic) as a Git submodule. This has basically two advantages. I can easily benefit from new releases
simply by synchronizing my fork and updating the module. Furthermore, if I add features or bug fixes to the theme that also others might find useful, I can
easily create a pull request.


#### Experience so far

So what is my impression after toying with Hugo for a couple of hours and writing my first blog post?

The installation is super easy and you quickly get to the point where you have set up a basic site that can be taken as a starting point for further
improvements. From the decision to try out Hugo to an already nice looking example site it took me around 1 hour.

The workflow is really awesome. Running ```hugo server``` generates the site to a directory and starts a web server to serve it. A watch dog recognizes any
changes to input files and triggers a re-build. In combination with the live-reload feature and a browser window on the second screen or split screen, you
can thereby get a WYSIWYG-like experience during writing.

Here Hugo's performance really excels. I do not care if the final build of my small site takes a second or a minute. But during writing I like to have a
regular look at the rendered result. And then even seemingly small generation times could easily get annoying. When saving changes to the file of this
(nearly ready) blog post the changes become almost immediately visible in my browser window. Hugo states total times of something between 7 and 20 ms. But I
also observed some hiccups. Now and then the watch dog fails to detect my changes. But this is no big deal --- I simply save again or restart the server.

The documentation makes an excellent impression. It is very detailed and I found answers to all my questions so far. To me it is great fun to explore all the
possibilities of Hugo and apply changes to the site layout. If you do not want to provide these changes as a pull request to the theme repository, Hugo
greatly supports this. Besides the theme directory there is an identically structured global site directory which takes precedence over the theme files.
E.g. if you wanted to add a keywords meta tag to the page header (which you [do not want anymore](https://yoast.com/meta-keywords/)) you would simply copy
`themes/academic/layouts/partials/header.html` to `layouts/partials/header.html` and add the following line
```html
<meta name="keywords" content="{{ delimit .Keywords ", " }}">
```
As your changes reside in a dedicated directory it is always immediately clear in what aspects your site layout deviates from the theme.

And what about syntax highlighting? A first try using standard Markdown syntax looks quite appealing:
```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello world!");
    }
}
```
In one of the next blog posts I will explore further capabilities like adding line numbers, folding etc.


For writing mathematical stuff you have basically all the math notation capabilities of $\\LaTeX$ available. First experiments work exactly as expected:
$$ x_{1,2} = -\\frac{p}{2} \\pm \\sqrt{\\frac{p^2}{4} - q} $$

Overall I can state that I am super happy with the decision so far! Let's see how this evolves when I get to know Hugo a bit better. :wink:


#### Hello World!

The bare site went online on May 11, 2018. This is my first blog post. Feels great to be prepared for easily providing more content! :rocket:
