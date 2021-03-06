## Website content for [www.athenian-robotics.org](http://www.athenian-robotics.org)

## Commands

* `make website` - Build the website in site/
* `make clean` - Deletes site/
* `make server` - Start the live-reloading docs server

## Updating Website

1) Make desired edits on content

2) Generate the website content into the /site directory:

```bash
$ make website
```

3) The above edits might include new pages, so add unversioned files to git:

```bash
$ git status 
$ git add -A
```

4) Commit the changes:

```bash
$ git commit -m "a message"
```

5) Push to master:

```bash
$ git push -u origin master
```






