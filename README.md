# daRkStudio is a package!
daRkStudio can now be installed as an R package.

## Installation

```r
remotes::install_github("rileytwo/darkstudio")
darkstudio::install_darkstudio()
```

# Overview

This is something I did for fun, and figured other people might enjoy this as much as I do.

I have little experience in writing css and javascript, and even less experience in building IDEs. I did most of the work in RStudio's DevTools, by selecting elements and changing their properties. So, if anyone would like to help out by contributing, please do! I'd love the help :smile:.

## This is not an editor theme

RStudio v1.2 introduced the ability to import [your own theme](https://rstudio.github.io/rstudio-extensions/rstudio-theme-creation.html). **daRkStudio is not an editor theme**, and does not change the syntax highlighting in the editor. daRkStudio is an *RStudio theme*, that changes the default appearance of the Modern and Sky *RStudio themes* when using a dark *editor theme* (this is set by having `rs-theme-is-dark: TRUE` somewhere in an `*.rstheme` file).

RStudio, by default, has three themes: Classic, Modern, and Sky (you can see for yourself by going to `Global Options -> Appearance -> RStudio theme`).
On RStudio's Support page, there is a fourth theme listed, called [Dark](https://support.rstudio.com/hc/en-us/articles/115011846747-Using-RStudio-Themes#dark-theme).

> The dark theme is a superset to the Modern and Sky themes that is activated whenever the Editor theme uses a dark palette.

Meaning, when the editor theme is dark (i.e. `rs-theme-is-dark: TRUE`), RStudio's panels, borders, tabs, and menus will be the same color if you select Modern or Sky as the RStudio theme.

If you're curious, they use a different palette when using a [light theme](https://support.rstudio.com/hc/en-us/articles/115011846747-Using-RStudio-Themes#modern-theme).

Classic, however, does not change its appearance, regardless of `rs-theme-is-dark: TRUE` or `rs-theme-is-dark: FALSE`.
I think this can be overriden, but I don't plan to do so here.

TL;DR: whether you have your RStudio theme set to Modern or Sky, daRkStudio will work as long as you're using a dark editor theme.

## Pics or it didn't happen

![DarkRStudio](inst/media/dark-rstudio.png)

Here, the RStudio theme is set to Modern (remember, Sky would work here as well), and the editor theme is using an `*.rstheme` with `rs-theme-is-dark: TRUE`.

## Installation

This used to not be an R package and required manual copying/moving/pasting files from one place to another. Now that `darkstudio` is an R package, installation and maintenance is much simpler. However, I've kept the old installation method in the README in case anyone would rather go that route.

### Recommended Method

You can install `darkstudio` by using `install_github()` from the `remotes` or `devtools` packages.

```r
# If you haven't installed remotes yet,
# install.packages('remotes')
remotes::install_github('rileytwo/darkstudio')
```

Or,

```r
# If you haven't installed devtools yet,
# install.packages('devtools')
devtools::install_github('rileytwo/darkstudio')
```

After installation, you'll need to activate the theme.

In the RStudio console, type the following:

```r
darkstudio::activate()
```

If the installation was successful, the function will return `TRUE`. Otherwise
an error will be returned.

### Old Method
**You may want to back up the original files.**

I recommend placing them into a folder, something like `before-daRkStudio`,
`RStudio-original`, `original-rstudio-files-that-were-there-before-i-started-using-this-awesome-theme` etc., somewhere outside of RStudio's file directory (so they won't be removed when you update RStudio!).

### macOS

```bash
git clone https://github.com/rileytwo/daRkStudio

cp "daRkStudio/darkstudio.css" \
    "/Applications/RStudio.app/Contents/Resources/www/darkstudio.css"

cp "daRkStudio/index.htm" \
    "/Applications/RStudio.app/Contents/Resources/www/index.htm"
```

### Windows

```powershell
git clone https://github.com/rileytwo/daRkStudio

Copy-Item "daRkStudio\darkstudio.css" `
    "C:\Program Files\RStudio\www\darkstudio.css" `
    -Force

Copy-Item "daRkStudio\index.htm" `
    "C:\Program Files\RStudio\www\index.htm" `
    -Force
```

You may not have the permission to copy or overwrite items in `C:\Program Files`.
If that's the case, run PowerShell in an elevated prompt (as an Adminstrator)
and try to copy the items to `C:\Program Files\RStudio\Resources\www\darkstudio.css`
again. If that doesn't work, try opening the daRkStudio folder from File Explorer, and manually copying the files to the `C:\Program Files\RStudio\Resources\www\` directory.

If you're STILL unable to copy the files (it's Windows, so who knows?) open an issue and I'll do what I can to help.

### Linux

It's been a while since I've used RStudio on Linux (Kubuntu 18.04), so I'm not sure if the paths shown below are still correct.
If you're using Linux and find that these paths no longer work, please open an issue or pull request.

```bash
git clone https://github.com/rileytwo/daRkStudio

cp "daRkStudio/darkstudio.css" \
    "/usr/local/rstudio/<version-goes-here>/resources/www/darkstudio.css"

cp "daRkStudio/index.htm" \
    "/usr/local/rstudio/<version-goes-here>/resources/www/index.htm"
```

## Updating

### Recommended Method

```r
darkstudio::update_styles()
```

### Old Method

If you cloned the repositories, `cd` into the direcory that contains this repo.

Execute `git pull --rebase`, and copy the files to `RStudio`'s `www` directory again.

If you run into any troubles, please file an issue.

## Uninstalling

```r
darkstudio::deactivate()
remove.packages('darkstudio')
```

## I love you

Thanks for checking out daRkStudio.

If you like it, you can show support by starring this repo.
Or, if you know someone who may like daRkStudio, tell them to check it out!
