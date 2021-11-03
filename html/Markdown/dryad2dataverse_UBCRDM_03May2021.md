## dryad2dataverse

---

## Where 

![Dryad2dataverse Image](/Images/dryad2dataverseLogo.png)

* Source: [github.com/ubc-library-rc/dryad2dataverse](https://github.com/ubc-library-rc/dryad2dataverse)
* Documentation: [ubc-library-rc.github.io/dryad2dataverse/](https://ubc-library-rc.github.io/dryad2dataverse/)

---

## Why 

Note:

* UBC's "primary" research data repository is a Dataverse repository at [Scholars Portal](https://dataverse.scholarsportal.info).

* Other UBC users have deposited their data sets into [Dryad](https://datadryad.org); there is a large UBC contingent of data there — over 500 studies

* Collection is split between two (or more, really) repositories

* Manual transfer of metadata would be painful and slow

---

## What

Note:

### The solution

* As all material in Dryad is public domain data (CC0) by the terms of their license agreeement, there is no impediment to adding these data sets to UBC's collection at Scholars Portal

* Except maybe the citation count that researchers now have to check their citations in more than one place, but could be resolved with GraphQL [Eugene]

---

### Desired goals

Note:

* Simple enough to be used by users with little or no programming experience
* Modular - not all components shold be required
* System neutral
* No requirement of server overhead
* Ideally, a piece of software that would run from the command line with basic information supplied by an end user
* Should be able to be daemonized or scheduled

---

## How

Note:

##Technical overview 

* Dryad and Dataverse both have relatively well documented Application Programming Interfaces (APIs), so it would make sense to use a programmatic approach to transfer the data.

---

## The steps

Note:

1. Create a metadata crosswalk.

	UBC Research Commons has experience with Dataverse mapping from both a migration from moving research data from UBC to Scholars Portal and from an old Dataverse installation to a new one.


2. Analyze the Dryad collection
	
	Using the Dryad API, analyse the collection to see if file transfers to Dataverse make sense (ie, are there too many large files).

3. User the native Dataverse JSON as import. More complex, but complete control over what goes where, which is not possible if using DDI or schema.org JSON

4. Start programming

---

## End result

Note:

* Pure Python 3 (v3.6 or higher)
* Limited dependency on external libraries
* Three modules
* Serialize -> Transfer -> Monitor
* Make some sort of diagram here

---

## The components

---


### dryad2dataverse.Serializer


Note:


* Serializer module connects to a Dryad instance and converts the Dryad JSON output to Dataverse JSON output
* Also includes the file JSON
* Technically hardest part; Dataverse JSON is "complex".

Eg: `dv['datasetVersion']['metadataBlocks']['citation']['fields'][x]['value']`, where x is an integer

Complex hierarchical struture based on the underlying database rather than a human-parseable JSON object

---

### dryad2dataverse.Transfer


Note:

Transfers to Dataverse are not necessarily straightforward; it's not possible to update a single metadata field, etc. Dryad2dataverse uses the Transfer object to hopefully get around many of the issues involved

* Transfers require some sort of Dataverse privileges
* Transfer is dependent on the Serializer
* Takes a Serializer instance (ie, a Dryad study) as an input
* Copies the entire Dryad study to Dataverse, using the mappings provided by Serializer
* Puts a copy of the Dryad JSON in the dataverse record so that comparisons can be made if required
* Assigns the "correct" date to a study
* Moves files over *as-is* as much as possible; they are not unzipped as Dataverse does by default
* Tries to mirror the Dryad structure as much as possible

---

### dryad2dataverse.Monitor

Note:

* The first two modules are fine for one-off transfers
* Dryad studies, like Dataverse, are not necessarily constant
* To track changes over time, the previous state must be kept so that there is a method of comparison

* Uses a portable sqlite3 database which stores Dryad and Dataverse metadata
* Monitors both file and metadata changes
* Produces a report of *what* has changed

* In conjunction with the Transfer object, can work to update material that has already been transferred.

---

### The database

![The database](Images/dryad2dataverse.relationships.real.large.png)
---

### scripts/dryadd.py

* The no-programming solution

Note:

* A command line program to convert, upload and monitor Dryad studies
* Takes institutional [ROR](https://ror.org) as input
* Requires zero knowledge of Python (with the exception of installation)
* If binary versions become available even that will not be required
* Completely self-contained
* Auto database copy on each run

---

## Features

Note:

* Email notification of new file changes and updates to multiple people
* Options to skip problematic studies
* Can be run at any interval desired by the user

---

## Limitations


Note:

* File spoofing is not perfect by any means. The best solution is to be a super-user and turn of file processing for problematic file types
* Files that are larger than the maximum upload size are ignored. This means that some files may not be transferred. This affected less than 2% of UBC's studies.
* **By design** studies are not published. This allows a manual curation step.
* Does not track and merge any metadata changes made on the Dataverse side


### Specific limitations in Dryadd.py

* Auto-mailer setup can be tricky and annoying
* Problems with Dryad API (ie, bad information out) may necessitate manually skipping problem studies

---

### ubc-library-rc.github.io/dryad2dataverse/ <!-- .element: style="text-align: left;"  --> 

Paul Lesack <!-- .element: style="text-align: left;"  -->  
University of British Columbia Library Research Commons<!-- .element: style="text-align: left;"  -->   
paul.lesack@ubc.ca<!-- .element: style="text-align: left;"  -->




