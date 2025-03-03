---
title: 'How the Scanner Works (v0.5.5)'
---

! This guide is a WIP write up of the new v0.5.5. Scan Loop. Do not use this as guidance for folder structure, this is subject to change. 

# File Layout
Kavita expects all series to be nested in a folder. The ideal layout is:
``` 
/library root/
┖──Series A/
     ┖──series a - v01.cbz
┖──Series B/
    ┖──specials/
         ┖──Artbook 1.cbz
     ┖──series b - v01.cbz
```


# The Scan Loop

### Step 1: Validate if we need to scan
- On all scans, we validate that all library folders are not empty and can be accessed. If they cannot, the scan is aborted. For a series, we also check the folder path on disk for the series exists, if it does not, we abort. 
- Next, (Fill out the other cache checks)

### Step 2: Scan the directories
- The scanner is pretty smart, it avoids as much work as possible by default. 
- For each folder (in a library or for a given series), we first check if the folder has changed since our last scan. This checks at a minute level, so seconds will be ignored. This validates on the Last Write Time of the folder. (Note: Last Write time requires scanning all nested folders to accurately report the last time that folder has changed)
- In each folder, we check for a .kavitaignore and parse if it exists. This allows Glob patterns to apply to the scanner and ignore certain files or folders. This applies recursively. See more [here]().
- The files are then reported for processing (Parser)

### Step 3: Processing files
- The library dictates the rules for the parser and there are different parsers for different file types. 
- The parser parses out any information from the files, these files are a list of files collected from the folder scan in the previous step and are assumed to be one series
- After parsing, we check any series need to be merged together. Merging might happen if there are ComicInfo's with `LocalizedSeries` tag which allows 2 different names to be merged together automatically. Note: If there are multiple series in one folder with localizedSeries tag, they will group incorrectly. We will log this, but not stop the scan. This is not a valid configuration.
- For each found series in the folder (should be one), we invoke a process series task

## Step 4: Process Series
- This is responsible for taking the processed data and updating the Database. This runs parallel with other process series tasks. This may make the logs difficult to understand.
- The first thing that needs to happen is find the series in the Database. This is done by checking against Series name and localized name. If neither exist, a new series will be created.
- In here, we do all the underlying db work and update fields, etc.
- Lastly we queue tasks to perform Cover Generation and File Analysis. These again will run in parallel and are scheduled on the same queue as other scan tasks. 


## Notes
- Having multiple series in one folder is not supported but does work. There are some caveats to this. If there exists a series in that folder that utilizes LocalizedSeries ComicInfo tag, then the series may group in an undexpected way. This will be informed to the user via the Log file, ie ``
- For series scan, if the series folder is no longer on the disk, the scan will be aborted. A library scan should be run which will delete the series. 