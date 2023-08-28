# ABAP

## Content
- [ABAP Keyword Documentation](#abap-keyword-documentation)
- [Clean ABAP](#clean-abap)
- [Selection Screen](#selection-screen)
- [ALV](#alv)
- [Processing Internal Data](#processing-internal-data)
  - [Timestamp](#timestamp)
- [File Handling](#file-handling)
- [Object Oriented ABAP](#object-oriented-abap)
- [Enhancements](#enhancements)
- [Debugging](#debugging)


## ABAP Keyword Documentation

> [ABAP](#abap) > [Content](#content) > [This section](#abap-keyword-documentation)

No code can be written if we don't know the syntax. So the place to understand syntaxes as well as to see some **examples** is the [**SAP - ABAP Keyword Documentation**](https://help.sap.com/doc/abapdocu_752_index_htm/7.52/en-us/abenabap.htm)


## Clean ABAP 

> [ABAP](#abap) > [Content](#content) > [This section](#clean-abap)

Whenever we write code, we must ensure the readability and maintainability of that code.
It's not a one-person game where you do a program and never touch it.
Many after us will come and will work on the same code. So we have to ensure that anybody can look at the code, understand what's happening, and then do the required modifications without wasting their time and breaking the program.

For that, we refer to [**Clean ABAP coding**](https://github.com/SAP/styleguides/blob/main/clean-abap/CleanABAP.md) concepts.


## Selection Screen

> [ABAP](#abap) > [Content](#content) > [This section](#selection-screen)

## ALV

> [ABAP](#abap) > [Content](#content) > [This section](#alv)

- [CL_SALV_TABLE example](https://gist.github.com/xphill/021a2446b042a38b1556)

## Processing Internal Data

> [ABAP](#abap) > [Content](#content) > [This section](#file-handling)

### Timestamp
SAP stores timestamps in UTC time (similar to GMT time).
If you deal with programs that create timestamp entries in DB records, you will notice a difference between the timestamp entry and the system time. This is because the system time is converted to UTC when storing the timestamp.

To generate a UTC timestamp from system time:
```ABAP
DATA lv_timestamp TYPE timestamp.
GET TIME STAMP FIELD lv_timestamp.

" In-line declaration
GET TIME STAMP FIELD DATA(lv_timestamp).
```

To convert a date and time entered by the user to a timestamp that can be used to compare and extract timestamp records from DB, we can use:
```ABAP
" Assume that you have 2 screen parameters P_DATE for date and P_TIME for time
CONVERT DATE p_date
        TIME p_time
        INTO TIME STAMP lv_timestamp
            TIME ZONE sy-zonlo.
```

To convert a UTC timestamp (probably when reading from DB) to date-time combination of user's time zone:
```ABAP
" Assume the UTC timestamp is in field LV_TIMESTAMP and you want to store converted values in LV_DATE and LV_TIME. 
CONVERT TIME STAMP lv_timestamp TIME ZONE sy-zonlo 
        INTO DATE lv_date
             TIME lv_time. 
```

Conversion syntax details are found [here](https://help.sap.com/doc/abapdocu_751_index_htm/7.51/en-us/abapconvert_time-stamp.htm)
Further code examples on SAP documentation can be found [here](https://help.sap.com/doc/abapdocu_751_index_htm/7.51/en-us/abenconvert_time_stamp_abexa.htm).

## File Handling

> [ABAP](#abap) > [Content](#content) > [This section](#file-handling)

## Object Oriented ABAP

> [ABAP](#abap) > [Content](#content) > [This section](#object-oriented-abap)

## Enhancements

> [ABAP](#abap) > [Content](#content) > [This section](#enhancements)

### Enhancements to Classes and Interfaces
[**This link from SAP**](https://help.sap.com/saphelp_snc700_ehp01/helpdata/en/58/4fb541d3d52d31e10000000a155106/frameset.htm) explains the different kinds of enhancements that we have for classes and interfaces.

What are [SAP user exits and enhancements](https://www.stechies.com/sap-user-exits-and-enhancements/) and how to find them.

[Pre-method / post-method enhancements](https://wiki.scn.sap.com/wiki/display/ABAP/Step+by+step+to+enhance+ABAP+code+via+post+exit)

## Debugging

> [ABAP](#abap) > [Content](#content) > [This section](#debugging)
