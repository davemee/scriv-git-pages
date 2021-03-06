# Introduction #

Version 20180617

Welcome to scriv-git-pages! This is a little book about how to use Scrivener to produce a little book on GitHub Pages.

I have had and admired the Scrivener app for a long time, and always wanted to write something using it. I’ve tried it a few times for NaNoWriMo, National Novel Writing Month, to some good effect but ultimately no novel. I’ve tried it for a few other efforts, and right now I’m using it to write another little book that you’ll never see.

Scrivener, as I understand it, was created for writing books. It is focused on producing a single integrated output for various publication formats, eBook, PDF, I don’t know what all. It’s very powerful and, though it is well organized, it is incredibly complex because of all that power. 

I mostly write web pages. If I were to publish one of those would-be novels, it would probably be on Leanpub, which expects separate chapters in separate files. Scrivener was not built for that purpose and its author doesn’t want to make it fit that purpose. Well, his house, his rules. 

Nonetheless, some of Scrivener’s users have found ways to do these things, and I really want to use it in a project, so I’m going to build on the ideas of others and figure out a way that works for me. Since I’m doing another project using GitHub Pages, and since Scrivener really is a complex beast, I had decided to document all my settings and approaches. Then it occurred to me to publish them. That will encourage me to be more complete and clear, and it may, I hope, be useful to others.

Here goes!

----

# Style, Scrivener's and Mine #

Scrivener allows you–indeed encourages you–to use paragraph and font styles. You can style your headers, indent your paragraphs, show text in bold or italic, just about anything you’d like to do. Its approach has two advantages at least.

First of all, you can lay out your work any way you wish, so that its screen appearance is whatever works best for you as you write. You can have a plain typewriter look, or a fully formatted finalized kind of look.

Second, Scrivener does a good job of exporting your style information to whatever publication format you may choose, and that’s quite a few formats:

![][ScreenShot2018-06-17at5.43.41AM]

Now, when I used to do all my writing in Microsoft Word (ptui!), I used styles extensively. Basically I created my document in the form it was going to have on paper. (We used paper a lot in those days. Most of you have probably at least heard of paper.)

Now, most everything I write is published on the Internet, and I write directly in Markdown, where you use printable characters to indicate style. If I want a word to be italicized, I enclose it in stars, like this: \**bold*\*, and so on. In other words, I write in plain text, with a simple visible formatting syntax.

As I work with Scrivener, I may find it useful to use its styles, and to figure out how to make them export to my publication format. I’m going to begin, however, in plain text.

In what follows, we’ll start with Scrivener in its default mode, and I’ll show you all the changes I make to get it to do what I want. I’m going to try to make minimal changes rather than run wildly through Scrivener’s carefully-planned defaults. With luck, that will leave me in a position to move closer to Scrivener’s center as time goes on.

----

# ToC and Pages #

It’s about time to think more seriously about breaking this little book up into pages, setting up a Table of Contents, and inter-page linking. As in all things, I’ll think about this broadly and try to go about it incrementally.

### Splitting

I’ve decided to split this little book into separate HTML files, one per Section. (We’ll describe below just what a Section is, but for now, it’s basically a chapter.) Scrivener can help with this to a degree: you can get it to put a special separator line between each section. What it won’t do is close a section file and automatically open a new one.

So the plan is to write a little script, probably in Ruby, to read our one big file, and create a bunch of little files.

### Titles

Right now, I’m using page titles in Scrivener, and I intend to compile them into the final documents. The alternative would be to type the title explicitly into each “chapter/page”, but I thought Scrivener can do this, why not try it. 

### ToC

So our Table of Contents might want to look like this:

1. Introduction
2. Style, Scriveners and Mine
3. Starting the Project

Each of those lines would, of course, be a link to the page with that chapter in it. (Or, if it’s all compiled together as one big page, which I am sure I don’t like from the samples I’ve already made, they could be links to anchors.)

Scrivener isn’t much help with this. It can build a table that includes calculated page numbers, but that’s only useful in the one big file mode, so it’s not for us.

I’ve found a way to get a list of titles as plain text lines, and I’ve even mangled one of those into a list of links using Sublime and a bunch of regexes. That wasn’t fun.

### Page Names

I can see two basic approaches to the page names. The top surely needs to be called `index`, but the others could be named like the page titles, or simply numerically. We have the titles, and they’ll be at the top of every page, so we can use them if we wish.

But is there any real advantage to me or to the reader between a file named 09.html and testing-the-compile.html? I’m not sure. Likely I’ll start with numeric ones and see what I think later.

### Anchors

I happen to know that GitHub does something fancy with headings, H2 and the like. If you have a heading “\#\#\# Page Names”, GitHub’s Jekyll conversion will add an HTML anchor of “page-names” to its HTML. That might come in handy, but seems more useful if we *don’t* make pages than if we do.

In any case, I think our next step has to be splitting the file and getting the initial split version up on GitHub. Grr. Writing is easier.

----

# Starting the Project #

We’re here to create a little “book”, showing how to create the GitHub pages you will be reading when this is all done. This chapter starts at the beginning, though it may not wind up being the first page of the “book”.

I’ve just started with a blank Scrivener project, which I named “GitHub-Pages” and saved in Dropbox/Apps/Scrivener, where my shared Scrivener projects live.

Right now, what I see on the screen looks like this:

![][ScreenShot2018-06-15at3.48.45AM]

I’ve got View > Text Editing > Show invisibles turned on right now. That’s making the paragraph markers and dots for spaces show up. I don’t usually have that on but wanted to talk about the defaults set so far.

I’m going to compile from Scrivener to MultiMarkdown, which is its compile form intended to produce, well, MultiMarkdown, which will be roughly what GitHub expects to make our pages. And although Scrivener lets you format your typing any way you like, and although we may play with that capability later on, I’m used to typing in a sans-serif font (presently Arial) with explicit returns between paragraphs. I’ve got Scrivener’s default formatting set up that way.

----

# Default Formatting #

You set your initial font and paragraph info in Scrivener > Preferences, (command-comma). My info looks like this:

![][ScreenShot2018-06-15at3.56.55AM]

To change that information, you can click the controls at the top of the paragraph, for example, to show the fonts panel:

![][ScreenShot2018-06-15at3.59.33AM]

I could change the face from Arial if I wanted to. I don’t. I am going to turn off the Show Invisibles, however.

Note in the Formatting window above that the two paragraphs, the quotation and the name, are adjacent. When you’re on that window, you could use Format>Paragraph>Line and Paragraph Spacing to put some inter-paragraph spacing in place. I don’t do that, because Markdown requires explicit blank lines between paragraphs, so making fake ones would just confuse me. If this paragraph confuses you, pretend you didn’t read it.

----

# Styles #

Scrivener lets you assign “Styles” to paragraphs, and you can control how those styles get compiled into the output. So, in principle, I could set up a “Heading 2” style such that when I format a paragraph with Heading 2, it would look different in my editor, and (I believe) I could make it compile with the ## in front of it that signify H2 to Markdown. For now, I’m not going to do that: I’m going to type my own Markdown marks, because I’m used to it.

----

# Sections #

Next, I’m going to set up my “book” chapter and section information. I have in mind a very simple structure: A document at the top level of Scrivener’s binder, like this one, will be a “chapter”, represented as a single GitHub page. In principle, that would be all you need.

However, Scrivener has this really nice cork board feature, where you can put virtual index cards down, each one representing a document, with the document title, and a synopsis, where you can write on the card what a proposed document will be about. You can see the card for this document in the top right of this picture:

![][ScreenShot2018-06-15at4.15.13AM]

Because I plan to use the cork board to organize this little book, I want to allow for a bit more structure than just documents at the top. I’d like to organize a few cards into a chapter, so my rule will be that a folder at the top level also represents a chapter, and documents inside that folder represent text inside that chapter. So, if a chapter has three ideas in it, there might be three cards representing those ideas, and then each card’s document would  have some paragraphs about that idea. 

Why do we care? Well, we’re getting ahead of ourselves a bit, but I have learned enough about Scrivener’s compile to think that I’d like my chapters, when compiled, to automatically include the chapter Title from the binder, as their heading. But for ideas within the chapter, I expect not to include the card title, instead leaving the idea transition and any subtitling to manual editing.

I could do all the titling manually, and in the end I may prefer that. But I’m trying to give Scrivener every chance to work for me, so I’m planning to use that much structure.

Let’s talk about how that has to be set up.

----

# Documents, Sections, Layouts #

Warning: I’m going to get the terms wrong here, but I’ll do my best to correct to Scrivener terms.

Each document in Scrivener is a “Section” and has a “Section Type” for compilation. Associated with each Section Type, there is a “Layout”, which tells Scrivener how to format the compiled output for that section. We’ll use that to control what comes out, to be fed into GitHub Pages.

You could do this incrementally, or later, but I think it’s best to set up our initial Section Types now. We’ll have two, initially, which I think I’ll call Section, and Sub-Section. We’ll set them up to be auto-assigned: top level documents and folders will get Section, documents at the next level down will get Sub-Section.

You set this up in Project > Project Settings, in the Sections tab:

![][ScreenShot2018-06-15at4.31.51AM]

I’ll use the plus and minus buttons to create mine:

![][ScreenShot2018-06-15at4.33.00AM]

Then we go over to Default Types by Structure to tell Scrivener about our folders and sub-documents. It starts like this:

![][ScreenShot2018-06-15at4.34.19AM]

That’s not what we want, quite. We’ll use that +levels button to provide more levels for files, and fill that in:

![][ScreenShot2018-06-15at4.35.50AM]

I think that should do the job for us. Root files is like where Scrivener’s Draft and Research folders are. Level 1 is documents like this, and Level 2 will be documents inside folders. 

We’ll worry about layouts pretty soon. I want to think a bit now about what else to put in this little book, and how to organize it. I may even be regretting the simplistic section layouts we just did, but I know it’s easy to change.

----

# Regrets, I've had a few #

Since I mentioned regrets, and since I always do “Programming in Public”, or in this case “Scrivening in Public”, here’s what’s on my mind. I’m going to start creating a few index cards on the cork board, to get a general idea of what might be in this little book. And it becomes clear right away that those ideas will fall into classifications, and some of them could be quite large.

For example, we may have some ideas about compiling to markdown. We may have some discussion about the details of layouts and prefixes and suffixes. We will surely talk about how to split the compiled document into bits, and we will probably do that manually at least once and then write a little script to do it and then embed that script into the Scrivener compilation.

I can imagine that this may mean that this little book will have sections, each section containing chapters, each chapter containing some kind of sub-documents like our current Sub-Sections. Maybe three levels instead of two.

We can change that setup at any time but it always seems best to get it right at the beginning, especially when we don’t know our way around the framework all that well. But I have enough experience with Scrivener to feel sure that we can’t get in too much trouble if we don’t do anything too radical. So we’ll let it ride. I do think I’ll create a folder and then test a compile.

----

# Testing the Compile #

I’ve created a folder, called Testing the Compile, and this document inside it, called Created the folder. In our final compilation, we’ll want the title of the folder to show up and not the title of this document. Now I’ll add one more document, to better test our Sub-Section notion.

This is being written in a second sub-document, called “Another couple of paragraphs”. The Scrivener binder looks like this:

![][ScreenShot2018-06-15at4.53.51AM]

This should be enough to let us see whether our sections are working right. Let’s look at the compile:

Just for grins, this is yet another sub-document, called Looking at compile. Here’s what the compile window looks like now:

![][ScreenShot2018-06-15at4.55.43AM]

Notice that the sub documents in the folder are called Sub-Section, just as we intended. That happened automatically, because of that structure setup we did. You can see that the Section Types are all shown in italic. That means they were automatically defined from structure. We could set them explicitly if we wanted to. But we don’t. I *would* like to see what the compiled text looks like right now, so I’ll let the compile go through.

I open the compiled markdown file in Sublime, my text editor, and it all looks pretty good, except that in addition to all the pictures showing up in line in the text, as they should, they are all at the bottom of the compiled file as well. It looks like this:

```
Just for grins, this is yet another sub-document, called Looking at compile. Here’s what the compile window looks like now:

![][ScreenShot2018-06-15at4.55.43AM]

Notice that the sub documents in the folder are called Sub-Section, just as we intended. That happened automatically, because of that structure setup we did. You can see that the Section Types are all shown in italic. That means they were automatically defined from structure. We could set them explicitly if we wanted to. But we don’t. I *would* like to see what the compiled text looks like right now, so I’ll let the compile go through.

[ScreenShot2018-06-15at3.48.45AM]: ScreenShot2018-06-15at3.48.45AM.png

[ScreenShot2018-06-15at3.56.55AM]: ScreenShot2018-06-15at3.56.55AM.png

[ScreenShot2018-06-15at3.59.33AM]: ScreenShot2018-06-15at3.59.33AM.png

[ScreenShot2018-06-15at4.15.13AM]: ScreenShot2018-06-15at4.15.13AM.png

[ScreenShot2018-06-15at4.31.51AM]: ScreenShot2018-06-15at4.31.51AM.png

[ScreenShot2018-06-15at4.33.00AM]: ScreenShot2018-06-15at4.33.00AM.png

[ScreenShot2018-06-15at4.34.19AM]: ScreenShot2018-06-15at4.34.19AM.png

[ScreenShot2018-06-15at4.35.50AM]: ScreenShot2018-06-15at4.35.50AM.png

[ScreenShot2018-06-15at4.53.51AM]: ScreenShot2018-06-15at4.53.51AM.png

[ScreenShot2018-06-15at4.55.43AM]: ScreenShot2018-06-15at4.55.43AM.png
```

That last bit, if compiled to HTML from Markdown, would look like a series of links to the PNGs. I’m not at all sure where that came from, but I’m not going to worry about it right now. 

No titles have come out as yet. Let’s deal with that just for fun.

To get the titles to come out, we need to do a bit of layout assignment. I think maybe we don’t need to create new layouts yet, we might just be able to tick some options. Let’s try, inside compile:

![][ScreenShot2018-06-15at5.07.22AM]

There’s already a layout defined, Text Section with Heading, that nearly does the job. I notice it’s using H1 (one # sign), but maybe that’s OK. Now the compiled Markdown looks like this:

```
Title: GitHub-Pages  
Author: Ronald Jeffries

# Initial Notes #

We’re here to create a little “book”, showing how to create the GitHub pages you will be reading when this is all done. This chapter starts at the beginning, though it may not wind up being the first page of the “book”.

I’ve just started with a blank Scrivener project, which I named “GitHub-Pages” and saved in Dropbox/Apps/Scrivener, where my shared Scrivener projects live.

Right now, what I see on the screen looks like this:

![][ScreenShot2018-06-15at3.48.45AM]

I’ve got View > Text Editing > Show invisibles turned on right now. That’s making the paragraph markers and dots for spaces show up. I don’t usually have that on but wanted to talk about the defaults set so far.

I’m going to compile from Scrivener to MultiMarkdown, which is its compile form intended to produce, well, MultiMarkdown, which will be roughly what GitHub expects to make our pages. And although Scrivener lets you format your typing any way you like, and although we may play with that capability later on, I’m used to typing in a sans-serif font (presently Arial) with explicit returns between paragraphs. I’ve got Scrivener’s default formatting set up that way.

# Default Formatting #

You set your initial font and paragraph info in Scrivener > Preferences, (command-comma). My info looks like this:
```

And so on. I notice it has included Title and Author at the top. There’s a way to turn that off, and I’d like to do that while I’m thinking about it.

Mumble mumble how do we turn that off. I knew that yesterday or the day before …

![][ScreenShot2018-06-15at5.12.50AM]

Ah, yes. In the tags subtab of compile, it lists the metadata. Way down in the lower right, you can delete and add the stuff it includes. It’s basically putting YAML at the top of your compiled document. That’s actually something you might want on another day. Today is not that day. I’ll delete those items now:

![][ScreenShot2018-06-15at5.14.54AM]

And sure enough, they’re gone from the top of the file. 

We could actually turn this into a GitHub Pages page right now. Maybe I’ll do that next. Right now, it’s time for a break. 

----

# Setting up the project #

If this is going to be about creating GitHub Pages in Scrivener, we’re going to need a GitHub project. Let’s set that up. We’ll call it scriv-git-pages, and make it public in case anyone ever reads this.

That’s done, and I’ve cloned the project to a folder in my Dropbox. Now we need to set up Pages. I think you do that in GitHub settings:

![][ScreenShot2018-06-15at9.24.21AM]

We need to decide whether to put this whole project in GitHub Pages or just the docs folder. I guess we’ll do the whole thing, since the whole project probably should be public. It’s set up and working.  The site address is [https://ronjeffries.github.io/scriv-git-pages/](https://ronjeffries.github.io/scriv-git-pages/). It looks like this:


![][ScreenShot2018-06-15at9.59.53AM]

A little research tells me that GitHub Pages will put the README.md as the home page of the site, *unless* you have an *index.md* file, in which case it’ll be used.

Let’s go for it! Let’s publish what we have right now, and put it in a page with a known name, which we’ll retain for historical purposes. (I wonder if anyone will ever read this. A conversation yesterday tried to assure me that my mission is to emit my own behavior and not worry about whether other people find it useful. Years of Irish Catholic upbringing, however, make that hard to do.

Thinking out loud here, I believe we’ll do two things. First, we’ll compile this, as is, to a convenient name like v20180615.md, namely today’s date. Then we’ll update the README, for now. Then, we’ll create an index file, etc., as time goes on.

It actually went up, and if you want to look at it, it’s at [https://ronjeffries.github.io/scriv-git-pages/v20180615.md/v20180615.html](https://ronjeffries.github.io/scriv-git-pages/v20180615.md/v20180615.html). Of course, you won’t know to look until we get things at least a bit better arranged. I’ll leave that file there, but a story goes with it.



That url, with /v20180615.md/v20180615.html, is what I had to use because of how Scrivener does a compile of an MMD, it needs to export all your pictures, and all your text, into the same folder. And the compile window has only one name field in it, so they create a folder with the name you give, and a markdown .md file of the same name, and then when GitHub compiles the site, you get that name with .html instead of .md. Thus the odd name.

Now what I’d *like* would be to have a folder name like `v20180615`, and the file name index.md, so that the URL could be something like `ronjeffries.github.io/v20180615/` and the implicit lookup for index.html would do the rest. So I looked in the manual and asked on the excellent Scrivener forum. Soon I got the answer, which was so odd and incredible that it took me four tries to understand and believe it. Hold on.

If the folder you compile into happens to have a name ending in `_mmd` or `-mmd`, then the name you put in the compile window, like `index.md` will be applied to the output file only. No subdirectory will be created, and all the files will just dump into your `_mmd` folder. This bizarre fact is actually documented, on page 530 of the Scrivener manual.

But wait, there’s more. 

![][ScreenShot2018-06-16at7.47.10AM]

Normally when MMD is compiled, I guess, they clear the folder and then fill it. Apparently that checkbox in the dialog above ensures that any other files in the folder are left alone: only the ones Scrivener creates are overwritten. The description of this seems to say that the _mmd trick also avoids the overwriting, and that setting the checkbox may write to the parent folder. It’s very confusing. I expect to destroy the GitHub pages at least once because of this.

However, what this suggests to me is that I can get a shorter URL for these early draft copies using the _mmd trick. I’ll try that right now, hoping to create this version right here. And before I do that, I’ll put a version marker at the very top of the book. Then I’ll compile it and push a copy. 

That works and it’s preserved at [https://ronjeffries.github.io/scriv-git-pages/v20180616_mmd/](https://ronjeffries.github.io/scriv-git-pages/v20180616_mmd/)

I think it’s time to start splitting up the files. I’ll publish a few more versions, or maybe subsets, as I do this, in case anyone is watching, and for historical purposes (that is, because I want to). But the main thrust will be to try to get a published multi-page version onto GitHub Pages ASAP.

To that end, I think I’ll just split this one big file into one file per section, and name them 01,02, and so on. That should be a simple-enough script.

The first thing is to get Scrivener to put a separator string between our files. It turns out that it knows how to do this. To do so, you need to be using your own output format, not one of the defaults. You begin by popping up a menu on the one to change (I’ve picked Default, since it’s what I’ve been using so far) and you get a copy. You can see Default Copy is already there, since I’ve already created my copy. 

![][ScreenShot2018-06-17at6.41.19AM]

Next step, we’ll edit this and give it a better name, RJ GitHub. And we get the message that it has no assigned layouts. I guess those aren’t copied. I’ll go through that process again, as described above.







----

# Appendices #

View > Text Editing > Show Titles in Scrivenings

Related Options in Scrivener Preferences (command comma)

![][ScreenShot2018-06-17at6.06.28AM]

Note especially “Do not show separators above titles”. Uncheck to get separators plus titles. 

[ScreenShot2018-06-17at5.43.41AM]: ScreenShot2018-06-17at5.43.41AM.png

[ScreenShot2018-06-15at3.48.45AM]: ScreenShot2018-06-15at3.48.45AM.png

[ScreenShot2018-06-15at3.56.55AM]: ScreenShot2018-06-15at3.56.55AM.png

[ScreenShot2018-06-15at3.59.33AM]: ScreenShot2018-06-15at3.59.33AM.png

[ScreenShot2018-06-15at4.15.13AM]: ScreenShot2018-06-15at4.15.13AM.png

[ScreenShot2018-06-15at4.31.51AM]: ScreenShot2018-06-15at4.31.51AM.png

[ScreenShot2018-06-15at4.33.00AM]: ScreenShot2018-06-15at4.33.00AM.png

[ScreenShot2018-06-15at4.34.19AM]: ScreenShot2018-06-15at4.34.19AM.png

[ScreenShot2018-06-15at4.35.50AM]: ScreenShot2018-06-15at4.35.50AM.png

[ScreenShot2018-06-15at4.53.51AM]: ScreenShot2018-06-15at4.53.51AM.png

[ScreenShot2018-06-15at4.55.43AM]: ScreenShot2018-06-15at4.55.43AM.png

[ScreenShot2018-06-15at5.07.22AM]: ScreenShot2018-06-15at5.07.22AM.png

[ScreenShot2018-06-15at5.12.50AM]: ScreenShot2018-06-15at5.12.50AM.png

[ScreenShot2018-06-15at5.14.54AM]: ScreenShot2018-06-15at5.14.54AM.png

[ScreenShot2018-06-15at9.24.21AM]: ScreenShot2018-06-15at9.24.21AM.png

[ScreenShot2018-06-15at9.59.53AM]: ScreenShot2018-06-15at9.59.53AM.png

[ScreenShot2018-06-16at7.47.10AM]: ScreenShot2018-06-16at7.47.10AM.png

[ScreenShot2018-06-17at6.41.19AM]: ScreenShot2018-06-17at6.41.19AM.png

[ScreenShot2018-06-17at6.06.28AM]: ScreenShot2018-06-17at6.06.28AM.png