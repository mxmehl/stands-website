Welcome to FOSDEM 2021. This year, we have an experimental digital-only setup for reasons I think you all know.

## General structure

The stands.fosdem.org exhibition website is a static website generated with [Hugo](https://gohugo.io/). There is a general part,
created by FOSDEM, containing an overview of each stand, a thematic ordering and some general information, and a stand-specific part.

We create the general part and will seed the stand-specific part with what you provided during your submission in the _project name.md_. You can
update the contents of the file (via a pull request), but please make sure you do not remove any of the variables in the _[front matter](https://gohugo.io/content-management/front-matter/)_, otherwise the generator
will crash.

We've asked for two repositories from you, one with the content (Hugo content files) and one with static files. These repositories do not have
to contain anything else but .md (or .html) files and images respectively. The stand pages will keep the theme we created.

However, if you wish to provide an added experience, you can link to other pages on your own website. We ask however that you (a) keep the stand
information on stands.fosdem.org, that (b) you make sure that visitors know they are not longer on the FOSDEM website and (c) they can easily go back to stands.fosdem.org (e.g. to look at other stands).

The structure in your directories is flat (no hierarchy in sub folders). If you wish to create additional hierarchical subfolders, please contact us
and we will set it up.

We automatically generate a link to your video repository and the chatroom.

Your stand will live under _stands.fosdem.org/stands/<your project>_.

## Directory structure

We will clone the repositories you provided in two locations (corresponding to the path _stands/<your stand>_).

 * `content/stands/<your stand>` - location of the content files ([Hugo documentation](https://gohugo.io/content-management/organization/)).
 * `static/stands/<your stand>` - location of any static files (images, logo's, etc.).

## Important files

### _index.md

 * `content/stands/<your stand>.md` - generated by our custom highly advanced (;-)) script based on what you provided in your submission.

The contents of the _.md_ file can be changed as you wish, but please make sure you do not remove any of the variables (changing the content
is fine) of the _front matter_, otherwise the generator will not work. Please do not change the theme or the layout.

#### Front matter

```
---
title: _Project_
themes:
 - _Theme (please do not change from the one already in the repository)_
website: _Your website_
logo: stands/_Project_/_Logo filename_
description: |
    _Short description of your project (5 lines)_

showcase: |
    _Showcase: explain why people should come to your stand. You can use HTML (p, ul, etc.)_

new_this_year: |
    _What has happened in 2020 to your project? You can use HTML (p, ul, etc.)_

layout: stand
---
```

### Any other files

All other files can by any content Hugo accepts (HTML, MD).

You must provide a _title_ parameter in the front matter of your other pages; otherwise the links will not work.


## Technical details

Whatever you put as content of any file (or the contents of _\_index.md_) will appear in the resulting HTML page as follows.
```
<html>
<head>
[FOSDEM Head]
</head>
<body>
[FOSDEM Header]
<div class="container">
    <div class="row">
        <div class="col">
            <nav aria-label="breadcrumb">
                <ol class="breadcrumb">
                   [FOSDEM Generated breadcrumb]
                </ol>
            </nav>
        </div>
    </div>
    <div class="row">
        <div class="col">
            [Your content]
        </div>
    </div>
</div>
[FOSDEM Footer]
</body>
</html>
```

We use Bootstrap (4.5) for styling, so you can as well. jQuery is included (for Bootstrap), so you can use it.

Please note that you cannot load any assets (images, css or js) from any other domain than stands.fosdem.org.

## Local development environment
To test your changes locally, this is what you can do (you'll need the Hugo binary).

1. Clone the repository.
2. Put your content directly in _content/stands/your stand_ and _static/stands/your stand_. We use submodules to link everything together, so your content must go there directly.
3. Run _hugo serve_.
4. Profit!

If you notice anything amiss, let us know via _stands\_at\_fosdem\_dot\_org_. Or open a pull request ;-)


## Feedback
We realise this is certainly not the best possible option, but while we are fairly confident we can organise a physical edition,
going virtual is new for us as well. If you have any ideas for improvements, feedback or anything else, please contact us
at _stands\_at\_fosdem\_dot\_org_. Or open a pull request ;-)
