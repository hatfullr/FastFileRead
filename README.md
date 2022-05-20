# FastFileRead
```
    Roger Hatfull 2022
    University of Alberta
    
    A class for reading data from text and binary files quickly. It
    can also handle binary files which contain text in their headers
    and/or footers.
    
    All input files must have regular columns of data. If a binary 
    file is provided, you must provide a corresponding numpy format 
    string for reading that file. See the NumPy docs for more info:
    https://numpy.org/doc/stable/reference/arrays.dtypes.html
    
    Only data types of float and int are supported for text files.

    Only files with regularly spaced columns are supported.

    If a binary file contains mixed types, the result will be a NumPy
    array that also has mixed types. This can result in 'TypeError:
    unhashable type' when trying to take a slice of data.

    Data can be accessed from a FastFileRead object using either keys
    like a dictionary if arguments are supplied to the keyword 'key',
    or by using indices or slices as with a list.
    
    If return_type is dict or np.ndarray, then the returned data can
    be accessed using keys with values that are set by the very last
    line in the header section that matches the number of columns in
    the first line of data. If keyword 'header' is 0, then the
    columns can be accessed using keywords 'col0', 'col1', etc. up to
    the total number of columns in the file.
    
             Name         Type                            Description
    -------------   ----------   ------------------------------------
         filename          str   The file or list of files to be read
                     list-like
    
           header          int   The number of lines to skip at the
                     list-like   top of each file. If the file is in
                                 binary format, this speicifes the
                                 number of bits to skip at the
                                 beginning of the file if the header
                                 lines are detected to be binary.
    
           footer          int   The number of lines to skip at the
                     list-like   bottom of each file. If the file is
                                 in binary format, this speicifes the
                                 number of bits to skip at the end
                                 of the file if the footer lines are
                                 detected to be binary.

         max_rows          int   The maximum number of rows to read
                          None   from each data file after skipping
                                 'header' number of rows. If set to
                                 'None' (default) all rows will be
                                 read.
    
    binary_format         None   The format to use when reading
                     list-like   binary files in 'filenames'. If
                           str   None, the file is assumed to be a
                                 text file.
    
       binary_EOL          str   The End Of Line format string used
                     list-like   in the input binary files.
    
           offset          int   Number of bytes to use as offset
                     list-like   when reading binary files.
    
        delimeter          str   Specify the delimeter that separates
                     list-like   the data columns. Default value None
                                 splits by whitespace.
    
    hdr_delimeter         None   Specify the delimeter that separates
                           str   the header columns. Defaults to
                     list-like   value of 'delimeter' if None.
    
      return_type         dict   Choose for the data to be returned
                    np.ndarray   as a list, NumPy array, or a
                          list   dictionary. Some types may be faster
                                 than others. If you choose 'list',
                                 then no headers will be returned.
                                 For np.ndarray and dict, the data
                                 can be accessed using keys
                                 corresponding to the labels found in
                                 the line of the header closest to
                                 the top of the data that matches the
                                 number of columns in the data.
    
              key         None   The reference name or list of names
                           str   given to each of the files in
                          list   'filename'. A file in 'filenames'
                                 can be accessed either using one of
                                 these keys.

         parallel         bool   If True, attempt to read each file
                                 using multiple processes. Sometimes
                                 this will make things faster, but
                                 not always.

           nprocs         None   The number of processes to use when
                           int   'parallel' is True. Set as None to
                                 use the most processes possible.

          verbose         bool   If True, prints the file path for
                                 each file read and how many seconds
                                 it took to read the file.
```
