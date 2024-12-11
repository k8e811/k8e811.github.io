+++
title = "S3 Archive"
date = "2024-12-11"
+++

Some organizations provide their public records by S3 buckets.  Budget minded
ones prevent viewing the entire history of objects.  This makes discovering
changes difficult.  This makes comparing versions of documents difficult.

ZFS provides a convenient way to snapshot a given sync of a bucket.
The `aws s3api list-object-versions` command gives a convenient way to list the
bucket for changes.  `git porcelain` provides a check check for changes because
the data is sorted.

There is a minor race condition that changes made between
`list-object-versions` and sync may be lost.  However, they'll appear in the
changes for the next snapshot.
