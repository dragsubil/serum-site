---
title: Writing Blog Posts
group: docs
order: 4
---

[Back to the index](%page:docs/index)

# Writing Blog Posts

Serum is a blog-aware static website generator and it provides an easy way to
write blog posts.

All blog post source files should be located under `posts` subdirectory of your
project directory. File name is not important to Serum, but it is recommended to
name your files like below, for a pretty directory listing when you are working.
If you don't care, that's fine.

```
YYYY-MM-DD-<title-slug>.md
```

* `YYYY` &mdash; Four digits of the year. (e.g. `2016`)
* `MM` &mdash; Two digits of the month, zero padded. (e.g. `05`, `11`)
* `DD` &mdash; Two digits of the date, zero padded. (e.g. `03`, `27`)

## Providing Metadata

At the beginning of each post source file, you need to write the post header
to define metadata of each post. The format of the header area can be found in
[Adding Pages to Your Website](%page:docs/pages) document. Currently there are
three post metadata you can define:

* `title` (string, required)

    Defines the title of the blog post. This title will be displayed in the
    title bar of a web browser and post listings.

* `date` (date and time, required)

    Defines the date and time when the post is written. The accepted formats
    are `YYYY-MM-DD hh:mm:ss` and `YYYY-MM-DD`.

* `tags` (comma-separated strings, *optional*)

    Defines one or more tags.

Following is an example of a valid source markdown file. Note that Serum doesn't
care about spaces between a comma and tags.

```
---
title: About GenServer in Elixir
date: 2017-06-15 13:27:00
tags: elixir,otp, study , foo
---

Lorem ipsum dolor sit amet ...
```

If you want to leave a post untagged, just drop the `tags: ...` line.

```
---
title: About GenServer in Elixir
date: 2017-06-15 13:27:00
---

Lorem ipsum dolor sit amet ...
```
