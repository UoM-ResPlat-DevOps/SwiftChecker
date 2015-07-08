## SwiftChecker:


usage: swift_checker.py [-h] [-c C] [-v] [-vv] [-w]
                        path container [object_or_path]

positional arguments:
*   path                  The full path to a file or directory that you would
                        like to check against a swift object or container
*   container             Name of the Swift container to check
*   object_or_path        Optional: For file comparison this is the specific
                        object name in swift to compare against. For directory
                        comparison, this is an optional prefix/path to append
                        to the begining of file names during comparison

optional arguments:
*   -h, --help            show this help message and exit
*   -c C, -credentials C  Full path to openrc file to read OpenStack/Swift
                        authentication credentials from
*   -v                    Verbose mode: Displays the md5 hashes of each file and
                        object. Display ETag calculation
*   -vv                   Very Verbose mode: Verbose mode + display the md5
                        hashes of individual segments
*   -w                    Use Windows style backslashes for object names

Single File Comparisons:

*    1. Example: Compare local file with object sharing the same name in swift container
       ./swift_checker.py filename container

*    2: Example: Compare local file with object having a differentname or path

       ./swift_checker.py filename container object_name

Directory Comparison:

*    3: Example: Recursively compare all files contained within alocal directory with
       objects in swift container

       ./swift_checker.py /absolute_path/to_my_files container

*    4: Example: Recursively compare all files contained within alocal directory with objects
                in swift container specifying the object name prefix

       ./swift_checker.py /absolute_path/to_my_files container my_objects_start_with/this/prefix/or/path


## SwiftEtag

usage: swift_etag.py [-h] [-s] filename segment_size

Description: Segment a local file and calculate MD5 checksums of each segment.
             Calculate OpenStack Swift Etag Checksum for segments.
             Useful for validating uploaded segmented objects with original file.

positional arguments:
*  filename      File to segment and calculate hash
*  segment_size  Segment Size in Bytes

optional arguments:
*  -h, --help    show this help message and exit
*  -s            write the individual segments to files on disk (default:
False)
