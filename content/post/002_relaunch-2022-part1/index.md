---
title: 'Site relaunch / part #1 🍻 😎🤘🏼'
subtitle: 'Update time: HUGO, Academic theme/Wowchemy'
summary: 'In part #1 of the posts on the site relaunch I will focus on the updates of HUGO and the Academic theme/Wowchemy. I will elaborate on how and why the integration of the Academic theme/Wowchemy with HUGO changed and what the implications are. I will describe how well this update worked for me.'
tags: [HUGO, Wowchemy, Academic]
categories: []
slug: site-relaunch-2022-02-part1
date: 2022-02-22T18:43:39+01:00
lastmod: 2022-02-22T18:43:39+01:00

image:
  caption: 'Bocca A Reta / Corsica'
---

## Everything screwed up 💩

_"Never change a running system"_ they say --- too bad it didn't run anymore. 😄  
The [initial setup](/post/creating-my-website-with-hugo) of this site was as follows:
- Repository #1 holding the site's actual content and the Academic theme referenced as a Git submodule. Together this made the input files for the HUGO build.
- Local installation of HUGO.
- Repository #2 holding the files of the readily built site. This repository was configured to be hosted via GitHub Pages.

This was a perfect example of _"works on my machine"_. After buying my shiny new laptop in December 2021, installing the current version of HUGO and cloning repository #1, I observed that the site failed to build locally. Apparently there have been breaking changes in the meantime. The Academic theme has been reworked completely, meanwhile known as [Wowchemy](https://wowchemy.com/), and the issues were basically everywhere:
- Application of the theme changed to a whole new approach.
- Configuration parameters for the site changed, both core HUGO parameters and theme-specific ones.
- Front matter parameters changed.
- Site widgets changed.

## Update time! 👻

So the task was to restore my capability of publishing content -- though I haven't been very productive in the past, I still want to be capable of doing so! 😉 This meant **updating HUGO and the Academic theme**, i.e. the technologies involved in producing the actual files of the site.

Since the initial site launch HUGO has evolved towards a modularized system with [HUGO Modules](https://gohugo.io/hugo-modules/) being the building blocks. Even a HUGO site is a module itself. And this is the path that Academic respectively Wowchemy [followed](https://wowchemy.com/blog/version-5.0-february-2021/#convert-your-site-to-use-hugo-modules): technically speaking Academic is no longer an actual HUGO _theme_ which you apply to your HUGO project. Instead, the Academic functionality has been incorporated into Wowchemy, which is a HUGO Module serving as the main building block of the site.

As you can imagine this transformation required some breaking changes. But the cool thing is: HUGO Modules (HUGO itself is written in Go) make use of [Go Modules](https://go.dev/blog/using-go-modules). In order to base your project on Wochemy you have to declare the dependency in the file `go.mod` in your site's root directory:
```
module github.com/wowchemy/starter-hugo-academic

go 1.15

require github.com/wowchemy/wowchemy-hugo-modules/wowchemy/v5 v5.0.0-20220220173604-a956bdff0252 // indirect
```

I very much like this approach, as I am able to pinpoint the specific Wowchemy version in a transparent manner and do not have to rely on the somewhat cumbersome Git submodules anymore. But arguably this is a personal preference. 

But after performing these updates, how did I fix my site's build with all the breaking changes in the configuration? First I tried to fix compiler error by compiler error. As this turned out to be very time-consuming, and I had the fear of missing new Wowchemy features, I took the opposite approach: I took an [example site](https://github.com/wowchemy/starter-hugo-academic/tree/master/exampleSite) as a base, hollowed it out, and added my poor existing content. This way I learned a lot about the new widgets and features.

Though the documentation of Wowchemy is very informative in general, I stumbled across a handful of spots where it wasn't up-to-date and listed outdated configuration parameters. This somehow diminished the otherwise good impression. But in my opinion, the fact that it is an actively maintained project weighs this out. In the end these were minor issues that could be easily worked around with a mix of Stack Overflow and inspecting the [Wowchemy sources](https://github.com/wowchemy/wowchemy-hugo-themes).

All things considered, I am very happy with Wowchemy. Site relaunch succeeded --- **cheers!** 🍻 
