---
category: Policy - Vision Zero
---
Bulk loading of CSVs into a database is something I've done on numerous occasions, so it made sense to learn how to do it properly. Typically this involves opening the CSV, reading each line, and then writing the line to the database. As the size of the files gets larger, it is more important that the import is done as efficiently as possible.

The SQLite [documentation](https://sqlite.org/faq.html#q19) provides some guidance on this. Instead of making a commit after each line, wrap the BEGIN and COMMIT statements around a group of insert statements to speed it up.

With some simple benchmarking, we can see that this makes a pretty big difference! Below, the first bloc of code:

