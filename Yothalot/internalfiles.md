# Yothalot internal file format

During the map/reduce algorithm, Yothalot writes intermediate results to
temporary files. The output from the mapper processes is for example written to
such intermediate files, which are used as input for the subsequent reducer
processes. These intermediate files generated by Yothalot store
[records](copernica-docs:Yothalot/record "Record") that have a key as identifier
and an array with the values. Moreover, these files have some useful properties:
they are compressed files that are splittable on 10MB boundaries. This means
that if you write data to such a file, you can later split up the file in 10MB
big parts, and each of these parts is a valid Yothalot file in its own right.
(i.e. records in a file do not cross 10 MB bounds, provided that a record is
smaller than 10 MB). This is different compared to most other compressed files,
because if you would cut a gzip compressed file into 10MB parts you end up with
corrupt unreadable parts.

You normally do not have to read or write such files yourself, as they are fully
managed by the Yothalot framework. But if you do want to create or read such
files too, you can use the [Yothalot\Input](copernica-docs:Yothalot/php-input "Input")
and [Yothalot\Output](copernica-docs:Yothalot/php-output "Output") utility classes.

