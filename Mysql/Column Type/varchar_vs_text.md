# Varchar vs Text

## TEXT

* fixed max size of 65535 characters (you cannot limit the max size)
* takes 2 + c bytes of disk space, where c is the length of the stored string.
* cannot be (fully) part of an index. One would need to specify a prefix length.

## VARCHAR(M)

* variable max size of M characters
* M needs to be between 1 and 65535
* takes 1 + c bytes (for M ≤ 255) or 2 + c (for 256 ≤ M ≤ 65535) bytes of disk space where c is the length of the stored string
* can be part of an index


## References

* [Difference between VARCHAR and TEXT in MySQL](https://stackoverflow.com/a/25301046)