# gowebly – A next-generation CLI tool for building amazing web applications in Go using htmx & hyperscript.

[![Go version][go_version_img]][go_dev_url]
[![Go report][go_report_img]][go_report_url]
[![Code coverage][go_code_coverage_img]][repo_url]
[![Wiki][repo_wiki_img]][repo_wiki_url]
[![License][repo_license_img]][repo_license_url]

**gowebly** description ...

Features:

- 100% **free** and **open source**.
- ...
- ...

## ⚡️ Quick start

First, [download][go_download_url] and install **Go**. Version `1.21` (or 
higher) is required.

Installation is done by using the [`go install`][go_install_url] command:

```console
go install github.com/gowebly/gowebly@latest
```

> 💡 Note: See the repository's [Release page][repo_releases_url], if you want
> to download a ready-made `deb`, `rpm`, `apk` or `Arch Linux` package.

Also, GNU/Linux and macOS users available way to install via 
[Homebrew][brew_url]:

```console
# Tap a new formula:
brew tap gowebly/tap

# Installation:
brew install gowebly/tap/gowebly
```

Next, run `gowebly` to create a new project:

```console
gowebly create built-in
```

Done! 🎉 Your amazing Go web app with [htmx][htmx_url] & 
[hyperscript][hyperscript_url] has been created.

### 🐳 Docker-way to quick start

If you don't want to physically install `gowebly` to your system, you feel
free to using our [official Docker image][docker_image_url] and run it from
isolated container:

```console
docker run --rm -it -v ${PWD}:${PWD} -w ${PWD} gowebly/gowebly:latest [COMMANDS]
```

## ✨ Usage

See the repository's [Wiki][repo_wiki_url] page to get general recommendations.

## 🧩 Commands & Options

### `create`

Command to create a new project with the given Go backend, [htmx][htmx_url] &
[hyperscript][hyperscript_url], and (_optionally_) with the most popular 
atomic/utility-first CSS framework (like [Tailwind CSS][tailwindcss_url], 
[UnoCSS][unocss_url] or else).

```console
gowebly create [BACKEND_NAME] [CSS_FRAMEWORK]
```

You cant choose a Go backend for your project:

| Backend name | Description                                                 |
|--------------|-------------------------------------------------------------|
| `built-in`   | Go backend with a built-in [net/http][net_http_url] package |
| `fiber`      | Go backend with the [Fiber][fiber_url] web framework        |
| `echo`       | Go backend with the [Echo][echo_url] web framework          |
| `chi`        | Go backend with the [chi][chi_url]  composable router       |

_Optionally_, you can choose CSS framework:

| CSS framework | Description                                         |
|---------------|-----------------------------------------------------|
| `tailwindcss` | Add [Tailwind CSS][tailwindcss_url] to your project |
| `unocss`      | Add [UnoCSS][unocss_url]  to your project           |

### `run`

Command to run your project in development mode only.

```console
gowebly run
```

In this mode, the following library versions will be supplied in Go HTML 
templates:

- **htmx**: from CDN by a simple `<script>` tag;
- **hyperscript**: from CDN by a simple `<script>` tag;
- (_optionally_) **CSS framework**: from CDN by a simple `<link>` tag;

> 💡 Note: In development mode, officially supported CDNs from developers 
> will be used ([unpkg][unpkg_url] for htmx and hyperscript, 
> [cdn.tailwindcss.com][tailwindcss_cdn_url] for Tailwind CSS, 
> [jsDelivr][jsdelivr_url] for UnoCSS).

### `build`

Command to build your project for production.

```console
gowebly build
```

The following library versions will be supplied in Go HTML templates:

- **htmx**: minified and embed to the `gowebly-body-scripts` block;
- **hyperscript**: minified and embed to the `gowebly-body-scripts` block after htmx part;
- (_optionally_) **CSS framework**: tree-shaking & minified, and embed to the `gowebly-head-styles` block;

## ❓ How it works

By default, `gowebly` CLI always search for YAML config file (`.gowebly.yml`)
in the current folder.

Every time you build your project by `gowebly build` command:

1. CLI scan and validate the given YAML config file (by default, search for 
   `.gowebly.yml` in the current folder), apply settings and options to the 
   current project;
2. Automatically download minified versions of **htmx** and **hyperscript** 
   from the official (and trusted) CDN resources;
3. Embed them into your Go HTML templates (inline-style) to the block called 
   `gowebly-body-scripts` (usually, placed on the bottom of the `<body>` tag);
4. (_optionally_) Prepare the tree-shaking and minified version of the chosen 
   **CSS framework** (via [Vite][vite_url]), and embed them into your Go HTML 
   templates (inline-style) to the block called `gowebly-head-styles` 
   (usually, placed on the bottom of the `<head>` tag);
5. CLI create a complex `docker-compose.yml` file in the root of the project 
   folder with instructions for deploy all of your project in isolated 
   containers via [Portainer][portainer_url] (strongly recommended) or 
   manually to your remote server.

That's it! Now, awesome **htmx** & **hyperscript**, and (_optionally_) **CSS 
framework** features are available in your Go HTML templates. Let's make 
awesome project and deploy it to the Internet 🚀

## ✨ Solving case

...

## 💡 Motivation

...

## 🏆 A win-win cooperation

And now, I invite you to participate in this project! Let's work **together** to
create the **most useful** tool for developers on the web today.

- [Issues][repo_issues_url]: ask questions and submit your features.
- [Pull requests][repo_pull_request_url]: send your improvements to the current.

Your PRs & issues are welcome! Thank you 😘

## ⚠️ License

[`gowebly`][repo_url] is free and open-source software licensed 
under the [Apache 2.0 License][repo_license_url], created and supported with 🩵 
for people and robots by [Vic Shóstak][author_url].

<!-- Go links -->

[go_download_url]: https://golang.org/dl/
[go_install_url]: https://golang.org/cmd/go/#hdr-Compile_and_install_packages_and_dependencies
[go_report_url]: https://goreportcard.com/report/github.com/gowebly/gowebly
[go_dev_url]: https://pkg.go.dev/github.com/gowebly/gowebly
[go_version_img]: https://img.shields.io/badge/Go-1.21+-00ADD8?style=for-the-badge&logo=go
[go_code_coverage_img]: https://img.shields.io/badge/code_coverage-0%25-success?style=for-the-badge&logo=none
[go_report_img]: https://img.shields.io/badge/Go_report-A+-success?style=for-the-badge&logo=none

<!-- Repository links -->

[repo_url]: https://github.com/gowebly/gowebly
[repo_issues_url]: https://github.com/gowebly/gowebly/issues
[repo_pull_request_url]: https://github.com/gowebly/gowebly/pulls
[repo_releases_url]: https://github.com/gowebly/gowebly/releases
[repo_wiki_url]: https://github.com/gowebly/gowebly/wiki
[repo_license_url]: https://github.com/gowebly/gowebly/blob/main/LICENSE
[repo_wiki_img]: https://img.shields.io/badge/docs-wiki_page-blue?style=for-the-badge&logo=none
[repo_license_img]: https://img.shields.io/badge/license-Apache_2.0-red?style=for-the-badge&logo=none

<!-- Author links -->

[author_url]: https://github.com/koddr

<!-- Readme links -->

[docker_image_url]: https://hub.docker.com/repository/docker/gowebly/gowebly
[portainer_url]: https://docs.portainer.io
[brew_url]: https://brew.sh
[unpkg_url]: https://unpkg.com
[vite_url]: https://vitejs.dev
[htmx_url]: https://htmx.org
[hyperscript_url]: https://hyperscript.org
[tailwindcss_url]: https://tailwindcss.com
[tailwindcss_cdn_url]: https://tailwindcss.com/docs/installation/play-cdn
[unocss_url]: https://unocss.dev
[jsdelivr_url]: https://www.jsdelivr.com
[net_http_url]: https://pkg.go.dev/net/http
[fiber_url]: https://gofiber.io
[echo_url]: https://echo.labstack.com
[chi_url]: https://go-chi.io
