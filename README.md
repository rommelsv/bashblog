bashblog-ng
========

This is the Next Generation version of (https://github.com/cfenollosa/bashblog). Me, and [lots of other people](https://www.google.com/search?q=%22Generated+with+bashblog,+a+single+bash+script+to+easily+create+blogs+like+this+one%22), love bashblog as a simple tool to maintain a blog. The reason for bashblog-ng is simply that I wanted more features added but did not want to pollute the original bashblog with lots of pull requests.

A single Bash script to create blogs. 

Created because someone wanted a very, very simple way to post entries to a blog by using a public folder on a server, without any special requirements and dependencies. Works on GNU/Linux, OSX and BSD.

You can see a sample here: (https://yagni.rocks). That page was 100% generated using bashblog-ng, no additional tweaking.

Check out [other bashblog-ng users](https://www.google.com/search?q=%22Generated+with+bashblog-ng+-+based+on+simple+greatness%22)


Usage
-----

Download the code and copy bb.sh into a public folder (for example, `$HOME/public_html/blog`) and run

    ./bb.sh

This will show the available commands. If the file is not executable, type `chmod +x bb.sh` and retry.

**Before creating your first post, you may want to configure the blog settings (title, author, etc).
Read the Configuration section below for more information**

To create your first post, just run:

    ./bb.sh post
    
It will try to use Markdown, if installed. To force HTML:

    ./bb.sh post -html
    
The script will handle the rest.

When you're done, access the public URL for that folder  (e.g. `http://server.com/~username/blog`) 
and you should see the index file and a new page for that post!


Features
--------

- Ultra simple usage: Just type a post with your favorite editor and the script does the rest. No templating.
- No installation required. Download `bb.sh` and start blogging.
- Zero dependencies. It runs just on base utils (`date`, `basename`, `grep`, `sed`, `head`, etc)
- GNU/Linux, BSD and OSX compatible out of the box, no need for GNU `coreutils` on a Mac.
  It does some magic to autodetect which command switches it needs to run depending on your system.
- All content is static. You only need shell access to a machine with a public web folder.
  *Tip: advanced users could mount a remote public folder via `ftpfs` and run this script locally*
- Allows drafts, includes a simple but clean stylesheet, generates the RSS file automatically.
- Support for tags/categories
- Support for Markdown, Disqus comments, Twitter, Feedburner, Google Analytics.
- The project is still maintained as of 2016. Bugs are fixed, and new features are considered (see "Contributing")
- Everything stored in a single ~1k lines bash script, how cool is that?! ;) 


Configuration
-------------

Configuration is not required for a test drive, but if you plan on running your blog with bashblog, you will
want to change the default titles, author names, etc, to match your own.

There are two ways to configure the blog strings:

- Edit `bb.sh` and modify the variables in the `global_variables()` function
- Create a `.config` file with your configuration values -- useful if you don't want to touch the script and be able to update it regularly with git

The software will load the values in the script first, then overwrite them with the values in the `.config` file.
This means that you don't need to define all variables in the config file, only those which you need to override
from the defaults.

The format of the `.config` file is just one `variablename="value"` per line, just like in the `global_variables()`
function. **Please remember:** quote the values, do not declare a variable with the dollar sign, do not use 
spaces around the equal sign.

bashblog uses the `$EDITOR` environment value to open the text editor.


Detailed features
-----------------

- HTML5 compatable
- Support for github username with corner-link
- A simple but nice and readable design, with nothing but the blog posts
- **NEW on 2.0** Markdown support via a third-party library.  
  The easiest method is to download
  Gruber's [Markdown.pl](http://daringfireball.net/projects/markdown/)
- Post preview
- Save posts as drafts and resume editing later
- HTML page for each post, using its title as the URL
- Configurable number of posts on the front page
- Automatic generation of an RSS file, feedburner support
- Additional page containing an index of all posts
- Automatically generates pages for each tag
- Rebuild all files while keeping the original data
- Comments delegated to Twitter, with additional Disqus support
- An option for cookieless Twitter sharing, to comply with the 
[EU cookie law](https://github.com/cfenollosa/eu-cookie-law)
- Google Analytics code support
- Contains its own CSS so that everything is reasonably styled by default
- Headers, footers, and in general everything that a well-structured html file needs
- Support to add extra content on top of every page (e.g. banners, images, etc)
- xhtml validation, CSS validation, RSS validation by the w3c
- Automatic backup of the site every time you post (stored as `.backup.tar.gz`)

Read the Changelog section for more updates or [check out the news on my blog](http://cfenollosa.com/blog/tag_bashblog.html)


Contributing
------------

Bashblog started at 500 SLOC and it now has hit the 1000 SLOC barrier. 
If we want to keep the code minimal and understandable, we need to make the difficult effort to restrain ourselves 
from adding too many features.

All bugfixes are welcome, but brand new features need to be strongly justified to get into the main tree. 
Every new request will be honestly and civilly discussed on the comments. 
As a guideline, pull requests should:

- Fix a use case for some people (e.g. internationalization)
- Add a use case which is arguably very common (e.g. disqus integration for comments)
- Be very small when possible (a couple lines of code)
- Don't require a significant rewrite of the code (Don't break `create_html_file()` or `write_entry()`, etc)
- It must work on Linux, BSD and Mac. Beware of using GNU coreutils with non-POSIX flags (i.e. `date` or `grep`)
- Follow the UNIX philosophy: do one thing and do it well, rely on third party software for external features, etc
- **Always** keep backwards compatibility when using the default configuration


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
