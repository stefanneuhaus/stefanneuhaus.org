# Stefan Neuhaus' Personal Website

I use [HUGO](https://gohugo.io/) and the [Academic](https://sourcethemes.com/academic) theme to create a static site from the content sources in this repo. A [GitHub Actions](https://docs.github.com/en/actions) workflow builds the site upon push and publishes it via [GitHub Pages](https://pages.github.com/).  
See the result at [https://stefanneuhaus.org/](https://stefanneuhaus.org/).

## Publish new Blog Post

1. Create new blog post: `hugo new --kind post post/my-article-name`
2. Start local, live-reload web server: `hugo server`
3. Open site at [http://localhost:1313/](http://localhost:1313/)
4. Write nonsense blog post ...
5. Publish:
```shell
git add .
git commit -m "Hey ... you nice blog post!"
git push
```

## License

The following files and directories including their contents are Copyright Stefan Neuhaus:

* `content/`

All other directories and files are MIT licensed unless clearly designated otherwise.
