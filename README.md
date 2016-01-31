**Warning: this is kinda experimental**

Active projects need active websites. An active website means we need content to
change easily and quickly, and this often means installing a CMS of some kind
(WordPress, MediaWiki, Drupal, Rails, etc). But projects end, and so does the
write activity on a website. People may still want to look at the website as a
record of what happened, but they are less interested in contributing new
content, since they project is, well, [finished].

To keep a record of the project you can be stuck keeping the CMS software up to
date so it doesn't get hacked, and making sure the database is upgraded and
backed up. As the Web gets older, this problem gets [worse].  Wouldn't it be
nice to replace the once dynamic site with a static version that wouldnt'
require software updates of any kind?

bagweb is a utility script for mirroring a website and writing the data into
a [BagIt] package for your data archive. The heavy lifting is done by [wget]
and [bagit.py] so you'll need to have those installed. bagweb really isn't
anything special, it's just a way of remembering a sequence of command-line
interactions.

    % bagweb http://mith.umd.edu/api-workshop/ api-workshop
    
    time passes ...

    % tree -L 2 apiworkshop
    apiworkshop
    ├── bag-info.txt
    ├── bagit.txt
    ├── data
    │   ├── apiworkshop.warc.gz
    │   └── mith.umd.edu
    ├── manifest-md5.txt
    └── tagmanifest-md5.txt

CAVEAT: If the website being archived has a lot of dynamic AJAX stuff going on,
the mirror copy may not be perfect, because wget doesn't execute JavaScript. But
it may work good enough for you, considering the alternatives.

[BagIt]: https://en.wikipedia/wiki/BagIt
[bagit.py]: https://github.com/libraryofcongress/bagit-python
[wget]: https://www.gnu.org/software/wget/
[worse]: http://www.newyorker.com/magazine/2015/01/26/cobweb
[finished]: https://www.youtube.com/watch?v=4vuW6tQ0218
