# Publishing standalone articles

Each article lives in its own folder and has a clean URL:
https://kaihuchen.github.io/articles/YourArticle/

1. Create a folder such as YourArticle (avoid spaces).
2. Write the article in README.md. Leave a blank line between HTML blocks and Markdown headings.
3. Put images and videos in the same folder and use relative paths.
4. Add index.md using the example below; change the title, description, and image.
5. Commit and push to main using GitHub Desktop. Wait for the GitHub Pages deployment to finish, then open the URL.

```liquid
---
layout: standalone-article
title: "Your article title"
description: "A short summary for sharing."
image: /YourArticle/banner.png
---

{% capture article %}{% include_relative README.md %}{% endcapture %}
{{ article | markdownify }}
```

Omit image if there is no banner. Edit README.md for future revisions; index.md renders it automatically. The shared layout is _layouts/standalone-article.html. It has no navigation, article directory, or links to other articles. Older articles keep their existing theme. Folder capitalization matters in URLs.

Video example:

```html
<figure>
  <video controls playsinline preload="metadata">
    <source src="demo.webm" type="video/webm">
    <a href="demo.webm">Download the video</a>.
  </video>
  <figcaption>Your video caption.</figcaption>
</figure>
```

## Comments and reactions

Standalone articles include Giscus automatically. Readers sign in with GitHub to comment or react. Discussions are stored in kaihuchen/articles under Announcements and matched to each article URL using strict pathname matching. Keep folder URLs stable to preserve their discussion association. Moderate comments at https://github.com/kaihuchen/articles/discussions.

To disable comments for one article, add `comments: false` to its index.md front matter. Older articles using other layouts are unaffected.
