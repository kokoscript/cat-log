# cat-log
a tiny book collection cataloging script

## Description
cat-log resolves ISBNs to short lines of information, and appends them to a file in tsv format. ISBN lookup is handled via the [OpenLibrary API](https://openlibrary.org/dev/docs/api/books).

## Usage
Before using cat-log, ensure you have awk, curl, and jq installed.

cat-log has two modes of operation: `add` and `bulk`. In `add` mode, a single ISBN is given to the script, like so:

``` bash
./cat-log add 0131103709 collection.tsv
```

This allows for adding books to the collection file one at a time. If you have many ISBNs and want to add them all to the catalog, `bulk` mode is used, like so:

``` bash
./cat-log bulk my-isbn-list collection.tsv
```

Each line in the ISBN list file should contain a single ISBN-13 or ISBN-10 on its own, without any dashes or characters aside from digits. Empty lines and lines starting with '=' are skipped.

If the specified collection file does not exist, cat-log will create it.

## Issues
cat-log was initially a personal project, only released in the hope that someone else may find it useful. As such, I haven't thoroughly tested certain edge cases; if you come across a book that breaks the script, feel free to open a PR or issue.
