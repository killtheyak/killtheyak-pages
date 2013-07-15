title: Contribute to Kill The Yak

1. Fork the [repo][].
2. Copy `template.md` to a new file.
3. Write your content. Commit.
4. Send a pull request.

Some things to note:

* You can write in [Markdown][].
* If your "recipe" has any dependencies, include them in `deps`. You can refer to other pages in the repo by writing their filename (without the extension), e.g. `deps: [install-homebrew]`
* Content enclosed in ` ``` ` is important. When other pages list your page as a `dep`, the content between the ` ``` ` will be included on their page.
* Don't forget to add yourself as a contributor so you can get credit! You can write your name, or you can write your Github page URL. 

For an example, here is what the template looks like:

<div class="codehilite"><pre>
title: Create my new page
updated: 2013-07-13
description: This is the template page.
os: [macosx, windows, linux]
tags: []
deps: [example-dep]
contributors: ["http://www.github.com/YOU"] 

Write your content below.

<pre>```
# Content goes here!
```</pre>
</pre></div>

Click [here][example] to see how it would get rendered.

[Markdown]: http://daringfireball.net/projects/markdown/
[repo]: https://github.com/killtheyak/killtheyak-pages
[example]: /template/