**Warning: this is kinda experimental**

Active projects need active websites. An active website is one that can be
updated quickly and easily, which often means installing a CMS of some kind
(WordPress, MediaWiki, Drupal, Rails, etc). But projects end, and so does the
write activity on a website. People may still want to look at the website as a
record of what happened, but they are less interested in contributing new
content, since the project is, well, [finished].

To keep the record of a project you are stuck keeping the CMS software up to
date so it doesn't get hacked, and making sure the database is upgraded and
backed up. As the Web gets older, this problem gets [worse].  Wouldn't it be
nice to replace the once dynamic site with a static version that wouldn't
require software updates of any kind?

bagweb is a utility script for mirroring a website, creating a WARC file, and
writing the data into a [BagIt] package for your data archive. The heavy lifting
is done by [wget] and [bagit.py] so you'll need to have those installed.  bagweb
really isn't anything special, it's just a way of remembering a sequence of
command-line interactions, and perhaps a modest preservation pattern for the 
Web.

    % bagweb http://mith.umd.edu/api-workshop/ api-workshop

    Crawling http://mith.umd.edu/apiworkshop/

    Finished, see /Users/ed/Projects/bagweb/apiworkshop.log for details.

    You may want to record additional provenance in
    /Users/ed/Projects/bagweb/apiworkshop/bag-info.txt

    % tree apiworkshop
    apiworkshop
    ├── bag-info.txt
    ├── bagit.txt
    ├── data
    │   ├── apiworkshop.warc.gz
    │   └── mith.umd.edu.tar.gz
    ├── manifest-md5.txt
    └── tagmanifest-md5.txt

You can take this bag and put it somewhere where you like to keep track of data.
Then you can scp the snapshot file, in this case
`apiworkshop/data/mith.umd.edu.tar.gz` and unpack it in place of the previously
installed CMS.

CAVEAT: If the website being archived has a lot of dynamic AJAX stuff going on,
the mirror copy may not be perfect, because wget doesn't execute JavaScript. But
it may work good enough for you, considering the alternatives.

[BagIt]: https://en.wikipedia/wiki/BagIt
[bagit.py]: https://github.com/libraryofcongress/bagit-python
[wget]: https://www.gnu.org/software/wget/
[worse]: http://www.newyorker.com/magazine/2015/01/26/cobweb
[finished]: https://www.youtube.com/watch?v=4vuW6tQ0218
