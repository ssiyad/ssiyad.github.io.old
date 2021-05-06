---
title: "Why Hugo"
date: 2021-05-05T04:09:20+05:30
---

I've used Jekyll for a long time. But then I met hugo and fallen in love with it. Here's why.

1. Simple  
it's easier to setup. You just have `hugo new site` and start writing in plain markdown.
Simple as that. Hugo doesn't bring that headache of having to learn new a completely new
ecosystem. When I tried Jekyll, I had to use [grunt](https://gruntjs.com/) to watch file
changes. Hugo does it with `--watch` command.

2. Fast  
Thanks to Go, hugo can generate pages in seconds. Even with `--disableFastRender` and 
`--ignoreCache`, it outperforms any other static site generators. Changes you make are
almost instant, making you feel awesome.

3. Templates  
One of hugo's strength comes from it's templates. It uses `html/template` and 
`text/template` by Go. These are used to generate code injection safe html docs. Most of the
template variables are easily understandable and context aware, making them easier to use.
    ```
    {{ $title := print .Site.Title " | " .Title }}
    {{ if .IsHome }}{{ $title = .Site.Title }}{{ end }}
    <title>{{ $title }}</title>
    ```
    This sets page title depending on it's type. Variables and conditionals are easier 
    enough to get started.

That's some of them, but there's more. Be sure to check out [Hugo Docs](https://gohugo.io/documentation/).
