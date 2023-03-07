bashblog-simple
========

Being simple is hard.
[bashblog](https://github.com/cfenollosa/bashblog), is an amazing but tool from
a single objective: being simple. Fortunately, license allows to share and use
different contributions to materialize that *simple* concept.
[bashblog-ng](https://www.github.com/dvwallin/bashblog-ng) already includes some
of said contributions to original project.
By March 2023, I'll fork both projects and include only those changes that
reflect my idea of simplicity at least for this blog.
Although github's repo is a for from original bashblog, I will add the '-simple'
suffix to the project.

Created because someone wanted a very, very simple way to post entries to a blog
by using a public folder on a server, without any special requirements and
dependencies. Works on GNU/Linux, OSX and BSD.

You can see a sample here: [blog.cuevano.org](https://blog.cuevano.org).

Check out [other bashblog-simple users](https://www.duckduckgo.com/search?q=%22Generated+with+bashblog-simple+-+%28B%29e+%28A%29wesome+%26+%28S%29imple+%28H%29omie%22)


Usage
-----

Download the code and copy bb.sh into a public folder (for example, `$HOME/public_html/blog`) and run

    ./bb.sh

This will show the available commands. If the file is not executable, type `chmod +x bb.sh` and retry.

**Before creating your first post, you may want to configure the blog settings (title, author, etc).
Read the Configuration section below for more information**

To create your first post, just run:

    ./bb.sh post

It will try to use Markdown, and only Markdown. So no html switches here.

The script will handle the rest.

When you're done, access the public URL for that folder (e.g. `http://server.com/~username/blog`)
and you should see the index file and a new page for that post!


How to...
---------

Please [read the wiki](https://github.com/rommelsv/bashblog/wiki) to learn
how to use the advanced features of Bashblog, such as headers and footers,
 static pages, and more.


Features
--------

- Ultra simple usage: Just type a post with your favorite editor and the script 
  does the rest. No templating.
- No installation required. Download `bb.sh` and start blogging.
- Simple dependencies. It runs just on Markdown.pl + (base + core)  utils
  (`date`, `basename`, `grep`, `sed`, `head`, `find`, etc).
- Linux, actually just Ubuntu 18.04. If you like to test it in your system: be
  my guest.
- All content is static.
- Allows drafts, includes a simple but clean stylesheet, generates the RSS file automatically.
- Support for tags/categories.
- Support for Markdown, Twitter, Feedburner.
- Support for a basic year/month filesystem kind of structure.
- The project is still maintained as of 2023. 
  As I've mentioned, my idea of 'simple'.
- Everything stored in a single ~1k lines bash script, how cool is that?! ;)


Configuration
-------------

Configuration is not required for a test drive, but if you plan on running your
blog with bashblog-simple, you will want to change the default titles, 
author names, etc, to match your own.

There are two ways to configure the blog strings:

- Edit `bb.sh` and modify the variables in the `global_variables()` function
- Create a `.config` file with your configuration values -- useful if you don't want to touch the script and be able to update it regularly with git

The software will load the values in the script first, then overwrite them with the values in the `.config` file.
This means that you don't need to define all variables in the config file, only those which you need to override
from the defaults.

The format of the `.config` file is just one `variablename="value"` per line, just like in the `global_variables()`
function. **Please remember:** quote the values, do not declare a variable with the dollar sign, do not use
spaces around the equal sign.

bashblog-simple uses the `$EDITOR` environment value to open the text editor.
So configure it in your initial shell script (i.e., ${HOME}/.bashrc,
${HOME}/.zshrc)


Detailed features
-----------------

- HTML5 compatible
- A simple but nice and readable design, with nothing but the blog posts
- Markdown support via a third-party library.
  The easiest method is to download
  Gruber's [Markdown.pl](http://daringfireball.net/projects/markdown/).
- Post preview.
- Save posts as drafts and resume editing later
- HTML page for each post, using its title as the URL
- Configurable number of posts on the front page
- Automatic generation of an RSS file, feedburner support
- Additional page containing an index of all posts
- Automatically generates pages for each tag
- Rebuild all files while keeping the original data
- Comments delegated to Twitter
- An option for cookieless Twitter sharing, to comply with the
  [EU cookie law](https://github.com/cfenollosa/eu-cookie-law)
- Contains its own CSS so that everything is reasonably styled by default
- Headers, footers, and in general everything that a well-structured html file needs
- Support to add extra content on top of every page (e.g. banners, images, etc)
- xhtml validation, CSS validation, RSS validation by the w3c
- Automatic backup of the site every time you post (stored as `.backup.tar.gz`)

Read the Changelog section for more updates or
[check out the news on my blog](http://blog.cuevano.org/tag_blog-announcements.html)


Contributing
------------

Bashblog started at 500 SLOC and it now has hit the 1000 SLOC barrier.
If we want to keep the code minimal and understandable,
we need to make the difficult effort to restrain ourselves from adding too many features.

All bugfixes are welcome, but brand new features need to be strongly justified
 to get into the main tree.
Every new request will be honestly and civilly discussed on the comments.
As a guideline, pull requests should:

- Fix a use case for some people (e.g., internationalization)
- Add a use case which is arguably very common
- Be very small when possible (a couple lines of code)
- Don't require a significant rewrite of the code (don't break `create_html_file()` or `write_entry()`, etc)
- It must work on Linux.
- Follow the UNIX philosophy: do one thing and do it well, rely on third party software for external features, etc
- **Always** keep backwards compatibility when using the default configuration

bashblog-simple:

I've started this repo from bashblog-ng.
I've noticed some of original pull requests to bashblog were included into
bashblog-ng. I am keeping history from there. So if your contribution it is not
included as it should be, open an issue, and we can work it out so it should be
recognized.


Changelog
---------
- 2.11     No google references. year/month filesystem structure.
- 2.10     Added `global_twitter_card_image`
- 2.9      Added `body_begin_file_index`
- 2.8      Bugfixes<br/>
           Slavic language support thanks to Tomasz Jadowski<br/>
           Removed the now defunct Twitter JSON API share count<br/>
           Support for static, not managed by bashblog html files<br/>
- 2.7      Store post date on a comment in the html file (#96).<br/>
           On rebuild, the post date will be synchronised between comment date and file date, with precedence for comment date.
- 2.6      Support for multiple authors, use a different `.config` for each one
- 2.5      Massive code cleanup by Martijn Dekker<br/>
           'tags' command<br/>
           The word 'posts' in the tag list (both website and command) now has a singular form, check out `template_tags_posts_singular`
- 2.4      Added Twitter summaries metadata for posts (#36)
- 2.3.3    Removed big comment header.<br/>
           Added option to display tags for cut articles on index pages (#61)<br/>
           Cleaned up "all posts" page (#57)
- 2.3.2    Option to use topsy instead of twitter for references
- 2.3.1    Cookieless Twitter option
- 2.3      Intelligent tag rebuilding and Markdown by default
- 2.2      Flexible post title -> filename conversion
- 2.1      Support for tags/categories.<br/>
           'delete' command
- 2.0.3    Support for other analytics code, via external file
- 2.0.2    Fixed bug when $body_begin_file was empty.<br/>
           Added extra line in the footer linking to the github project
- 2.0.1    Allow personalized header/footer files
- 2.0      Added Markdown support.<br/>
           Fully support BSD date
- 1.6.4    Fixed bug in localized dates
- 1.6.3    Now supporting BSD date
- 1.6.2    Simplified some functions and variables to avoid duplicated information
- 1.6.1    'date' fix when hours are 1 digit.
- 1.6.0    Disqus comments. External configuration file. Check of 'date' command version.
- 1.5.1    Misc bugfixes and parameter checks
- 1.5      Đurađ Radojičić (djura-san) refactored some code and added flexibility and i18n
- 1.4.2    Now issues are handled at Github
- 1.4.1    Some code refactoring
- 1.4      Using twitter for comments, improved 'rebuild' command
- 1.3      'edit' command
- 1.2.2    Feedburner support
- 1.2.1    Fixed the timestamps bug
- 1.2      'list' command
- 1.1      Draft and preview support
- 1.0      Read http://is.gd/Bkdoru




License
-------

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
