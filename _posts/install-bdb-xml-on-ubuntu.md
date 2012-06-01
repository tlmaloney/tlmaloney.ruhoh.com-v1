---

title: Installing BDB XML in Ubuntu
date: '2012-06-01'
description: Installing BDB XML in Ubuntu
categories: sysadmin
tags: 
    - ubuntu
    - precise
    - bdb
    - xml

layout: post

---

Installing BDB XML in Ubuntu
---------------------------

Read [this](http://zeth.net/post/350/) for a little introduction to BDB XML.

Download BDB XML from [Oracle's web site](http://www.oracle.com/technetwork/products/berkeleydb/downloads/index.html). You'll need to create a login (free) if you don't have one already.

Decompress the downloaded file:

	cd ~/Downloads
	tar xvfz dbxml-2.5.16.tar.gz

Before building the source, modify one of the files:

	~/Downloads/dbxml-2.5.16/xqilla/include/xqilla/framework/XPath2MemoryManager.hpp

In the file, after line 26 add a line with

	#include <cstddef>

After which you can now build:

	cd dbxml-2.5.16/
	sh buildall.sh

More build options can be [found here](http://docs.oracle.com/cd/E17276_01/html/ref_xml/xml_unix/intro.html)

Once compilation is complete, the dbxml binary is located in

	~/Downloads/dbxml-2.5.16/install/bin/

I suggest either moving the binary, or making a symlink:

	ln -s ~/Downloads/dbxml-2.5.16/install/bin/dbxml ~/bin/dbxml