# Quality-Manual
Quality manual WIP

You can view the current latest build of the document [here](http://quality-manual.s3-website-eu-west-1.amazonaws.com/index.html)
There is also a [PDF](http://quality-manual.s3-website-eu-west-1.amazonaws.com/Main.pdf) of the document a [DocBook](http://acecentre.github.io/Quality-Manual/Main.xml) and [Word Docx](http://quality-manual.s3-website-eu-west-1.amazonaws.com/Main.docx) version available.

##Instructions for editing

1. Clone the repo locally
``git clone https://github.com/ACECentre/Quality-Manual.git``

2. Edit the Main.adoc and associated files. You can use any text editor. Follow the [asciidoctor syntax](http://asciidoctor.org/docs/asciidoc-syntax-quick-reference/). I recommend though installing [Atom](https://atom.io) - a editor that supports asciidoctor well. If you do use Atom you may also want to install the asciidoctor-preview package in atom if you want a nice pretty preview of your working document.

3. commit to git as you go!

4. When you commit [travis-ci](http://travis-ci.org) automates the build of the document to a [web-page](http://quality-manual.s3-website-eu-west-1.amazonaws.com/index.html) and [DocBook](http://quality-manual.s3-website-eu-west-1.amazonaws.com/Main.xml)

NB: Install [asciidoctor](http://asciidoctor.org/#installation)  ``gem install asciidoctor`` if you want to play around on the command line.
