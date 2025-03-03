---
title: 'Managing your files'
taxonomy:
    tag:
        - Metadata
        - ComicInfo
        - Naming
        - Scan
        - 'Refresh Covers'
metadata:
    'og:description': 'This page covers everything related to file management. This includes proper naming, local metadata, and how to update files in Kavita.'
    'og:title': 'Managing your files | Kavita Wiki'
    'og:url': 'https://wiki.kavitareader.com/en/guides-rework/managing-your-library'
admin: {  }
---

#### Page overview
[Naming convention / File Structure](#file-structure)<br/>
[Metadata](#metadata)<br/>
[Scanning files](#scanning-files)<br/>

<hr style="border:5px solid #4ac694"> </hr>
## File Structure
It's important to know how Kavita parses the info from the files.

Kavita uses parsing (not folder structure) to determine what is a series and what belongs to each series. Due to this, you are not required to put all of one series in the same folder, however, it is good practice.

Folder and File Structure TOC:
* [Comic File Structure](https://wiki.kavitareader.com/en/guides/managing-your-files/comics)
* [Manga File Structure](https://wiki.kavitareader.com/en/guides/managing-your-files/manga)
* [eBooks File Structure](https://wiki.kavitareader.com/en/guides/managing-your-files/ebooks)
* [PDF File Structure](https://wiki.kavitareader.com/en/guides/managing-your-files/pdf)
* [Raw Images File Structure](https://wiki.kavitareader.com/en/guides/managing-your-files/raw-images)

For all types of libraries, Kavita has an override for treating files as Specials. 

To force a Special status, the filename can use SP01, SP02, etc.

    /libraryroot/Series Name/Series Name SP01.cbz
    /libraryroot/Series Name/Specials/Series Name SP01 Special Name.cbz

This will take the file and force it to be a special. For it to identify as a special and not as the series from the filename, it will look up towards the library root and attempt to parse the series name from the folder names.<br/>
For example: `/libraryroot/Again!!/Specials/Again The After Story SP01.cbz`
will parse "`Again!!`" for the Series name and group the file as a special under Again!!

<hr style="border:5px solid #4ac694"> </hr>
## Metadata
Kavita uses metadata to parse Series Name, Volumes, Chapters...
Kavita reads metadata from within your archives (cbz, cbr, c7, cbt) and epub files. If your archives contain metadata, it will override any parsed information from the file. 

<hr style="border:2px solid #4ac694"> </hr>
### Comics and Manga
Comics and manga use a ".xml" file at the root of the cbz, cbr, cbt, cb7 files

This file must be named ComicInfo.xml and be at the root of the archive.

The XML schema of this file can be found in the [Anansi Project webpage](https://anansi-project.github.io/docs/comicinfo/schemas/v2.1). We support v2.1 (draft).

You can find multiple tools to add metadata under [Misc section](https://wiki.kavitareader.com/en/guides/misc#external-tools)

<hr style="border:1px solid ##465176"> </hr>
#### How Kavita parses certain ComicInfo tags

##### Age Rating

Age rating may vary between different files within a series. The Series will take the highest Age Rating (aka most mature) and use it from the files contained within. So for example, say you have:
* Issue 1 - PG
* Issue 2 - PG
* Issue 3 - M
The series will be M as that is the most mature rating in all Issues.

##### Count

In order for a Series to give a publication status, if you have at least one "Count" defined within any ComicInfo from the series and it is not 0, then Kavita will assume the Series is Completed. Otherwise, it will be assumed Ongoing.
Ideally, the value of this field should be the total number of volumes (manga) or issues (comics)

##### Release Year

Likewise with Age Rating, Release Year is a summation of the minimum year defined within a series that is at least 4 units long (> 1000).

##### Format
If a Format is specified, that issue or volume may be forced into being treated as a Special (v0.5.4+). The following entries will cause this:
* Special
* Reference
* Director's Cut
* Box Set
* Box-Set
* Annual
* Anthology
* Epilogue
* One Shot
* One-Shot
* Prologue
* TPB
* Trade Paper Back
* Omnibus
* Compendium
* Absolute
* Graphic Novel
* GN
* FCBD 

<hr style="border:2px solid #4ac694"> </hr>
### eBooks
EPUB files do not have a ComicInfo.xml, but they do have some limited metadata in the OPF file. Kavita tries to map as much of this information as possible. 

The tags that Kavita parses are:
* EPUB Tag (ComicInfo field)
* Description (Summary)
* Creators (Writer)
* Publishers (Publisher)
* Publication Date (Month, Day, Year)
* Title (Title)
* Subjects (Genre)

<hr style="border:5px solid #4ac694"> </hr>
## Scanning files
Scanning a library makes Kavita check its folders and sub-folders for new or removed items (books, archive files, etc). If new media is found, it then pulls it into the library. <br/>You can think of scanning as “check for new or changed content”. 
! **Important**:<br/>- First scans are often slow, especially on networked storage. Be patient<br/>- The Kavita Homepage and Library info, will be updated throughout the scan **in chunks of 50 series at a time.** <br/><br/>
! **Note**: Kavita performs a first-time scan on newly created libraries

<hr style="border:2px solid #4ac694"> </hr>
### What happens during a Scan?
Kavita will generate a library representation of your files on disk. A Kavita library does _not_ represent exactly your folder structure. Kavita uses filenames and some limited folder names to parse out the series, volume, chapter, etc from the file and group them.

The scan parses the file names, reads the comic info (if applicable), updates the database with that information, and updates the UI. 
If the file hasn't been modified since the last time we scanned, Kavita will not do extra processing on the file. 
If your archives contain metadata, it will override any parsed information from the file.

<hr style="border:2px solid #4ac694"> </hr>
### Refresh Covers
During the refresh covers task, the same kind of logic applies. This is a heavy task because of the amount of I/O we have to perform and because of the amount of memory we need to copy images out of the archive and onto the disk.
In this task, Kavita doesn't open up any archives if they haven't been modified unless you start a cover refresh from the UI. Even if the archive was modified, if you've locked the cover image by using the UI to upload your own custom cover, the archive will not be opened.


<hr style="border:2px solid #4ac694"> </hr>
### Analyze Files
During the analyze files task, Kavita will open epub files and count the number of words per entity. This is I/O and memory intensive. Like other tasks, Kavita employs checks against Last Modified to avoid re-calculation whenever possible. When invoking this task manually from the UI, it will force a recalculation, so be very careful if you use remote storage or a slow server.