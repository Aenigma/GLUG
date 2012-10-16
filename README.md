# About
This is the sourcecode for a website intended to assist people in learning the
basics of a a typical GNU/Linux distribution with a focus on Debian based ones.

# Set up
To be able to set this up, you're going to need a complete Ruby installation.
Because of that, it is probably ideal to try to use this using a UNIX-like which
work a lot better with Ruby than Windows. To install Ruby on a real system,
follow the instructions provided [here][rvm]. If you want to try to do it with
Windows, follow the instructions provided [here][rubyinstaller].

It boils down to installing rvm by using this command:

    $ curl -L https://get.rvm.io | bash -s stable --ruby

Then, you need to go to the project root and do a:

    $ bundle install

If that all worked, then you can proceed to run the server using:
    
    $ middleman server

If you want to generate the HTML files, go ahead and do a:

    $ middleman build

Which will create a `/build` directory in the root and populate it.

# Modifying
To modify the contents of the server you should know at least [HAML][haml],
[Markdown][markdown], [YAML][yaml], and basic [HTML/CSS][w3c].

## Layouts

The software being used to generate the web directory is [Middleman][middleman]
and, thus, its documentation should prove useful. Middleman is able to use
HAML template files to assist in having consistency. Thus, all the haml files
you create don't need to have a much boilerplating to include the navigation bar
and other components provided by the layout. If you'd like to change the layouts
themselves, have a look in `source/layouts`. They are regular HAML files with a 
`=yield` which gets replaced by the content of another HAML file.

The relation between HAML file and layout is configured in `config.rb`. The
default layout is called `layout.haml`.

### Styling
If you want to modify the styling used in the website, most (if not all) of the
code doing that is taken from [Twitter Bootstrap][bootstrap] so you should
definitely check it out its documentation. The files in question, of course,
are in the `css/` and `js/` directories.

## Metadata
In addition to all of this, the layouts have Ruby code embedded to help with
some automation. For one, certain [metadata][yamldata] about the article can be embedded into the page's HAML file at the top. Currently, `title`, `authors`,
`sections`, and `dropdown` are recognized. For a good example of these fields
being used, you should look through the source for `/doc/commands.haml.html`.

### Data Directory

Certain data is stored within a special directory called `data` in the root of
the project directory. These files can be [JSON][json] files or YAML files and
are specified using the base name of the file within a HAML file or HAML layout
file. These are typically used for metadata that would be used for multiple
pages. One example is the `authors.json` file which contain an index of
recognized author names. When an author is named from the local YAML data, the
name is looked up from this list and his/her website can be retrieved.

# Contributing
See [here][git].

[bootstrap]:http://twitter.github.com/bootstrap/
[git]:https://help.github.com/
[haml]:http://haml.info
[json]:http://www.w3schools.com/json/default.asp
[markdown]:http://daringfireball.net/projects/markdown/dingus
[middleman]:http://middlemanapp.com/
[rubyinstaller]:http://rubyinstaller.org/
[rvm]: https://rvm.io/rvm/install/
[w3c]:http://www.w3schools.com/html/default.asp
[yaml]:http://en.wikipedia.org/wiki/YAML
[yamldata]:http://middlemanapp.com/metadata/local-data/
