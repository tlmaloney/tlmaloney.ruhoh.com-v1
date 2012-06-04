---

title: BDB XML container and query tutorial
date: '2012-06-01'
description: Create a BDB XML database file from yahoo-example.xml
categories: sysadmin
tags: 
    - ubuntu
    - precise
    - bdb
    - xml
    - index

layout: post

---

Create a BDB XML database
----------------

First create a folder where your database files will live. Execute

	mkdir -p ~/dbxmldev

And nagivate into that directory:

	cd ~/dbxmldev

Start up dbxml. Execute

	dbxml

### Database creation

Create a new database container. At the prompt, execute

	dbxml> createContainer example.dbxml

Add an XML document:

	dbxml> putDocument yahoo-example '/path/to/example.xml'

Add an index corresponding to the deal level:

	dbxml> addIndex "" dealLevel node-element-equality-double

Now we can query our database, by for instance, finding all deal levels above a certain threshold. Let's find all deal levels above 620:

	dbxml> query 'collection("example.dbxml")/quoteEvents/quoteEvent[dealLevel > 620]'
	dbxml> print