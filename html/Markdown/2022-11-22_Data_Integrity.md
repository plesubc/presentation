<style>
.container{
  display: flex;
}
.col {
  flex: 1;
  vertical-align:top;
  /*text-align: left*/
}
.left {text-align:left !important;}
.top {vertical-align:top !important;}

</style>
<!--
# Title 
### Academic subtitle

## Authors etc. 

Examples:

* What has changed in a data release — Sept 28, 2018:

		Hi,

		I have a question about this new data release.

		If the ASCII data hasn’t changed, nor the SAS, SPSS and Stata code which are presumably used to generate the .sas7bdat, .sav and .dta files, how are the new files different from the old? Is there a changelog available so that users of these files can see any differences?

* Weird random files — Jan 8, 2019:

		In the December LFS, there’s an ASCII file corr1218.prn. What does this file represent? It didn’t appear in any of the previous months, and the filename implies some sort of correction, and there are the same number of records.

* [New] versions of files — May 27,2020:
In this case, the plain text file didn't change but the SAS/SPSS files did.

		So, because of this, all of the .sav, .sas7bdat and .dta files are also changed, presumably, as they are presumably created from the syntax (as per the screenshot attached, showing the old and new files).

		Technically, then, the flat ASCII file is unchanged but the data files derived from the ASCII files *are* different.

		Unless I’ve missed something, though, the folder /MAD_PUMF_FMGD_DAM/Root/5311-CPSS-SEPC-S1/Data_Données/RAW appears to no longer actually contain a data file, where it formerly contained one called “PUMF2020_CPSS_SEPC_S1.txt”

		That could pose a problem for someone who hasn’t had a chance to download it yet.

* Verifying downloads — Jan 15, 2021:

		This is what we have at UBC:

		-rw-r--r--@ 1 paul  staff  378101380  6 Jan 10:05 pccfNat_fccpNat_112020.txt

		----------------------
		Information for file: pccfNat_fccpNat_112020.txt
		Number of lines: 1734410
		Maximum line length 218, constant records
		----------------------

		The DLI FTP site (/MAD_PCCF_FCCP_DAM/Root/2016/pccf-fccp/pccf_2020_11_fccp)  is reporting the size as 378101380 bytes. 

* A better example for why this can be used to verify downloads — Feb 2 - 4,2021:

		Leanne’s right; the easiest way to ensure file integrity would be to have a file manifest with checksums (generally md5 or sha1)

		md5s can be generated any number of ways. The easiest:

		For Windows:
		In a command prompt window:

		CertUtil -hashfile <path to file> md5

		Mac:
		md5 <path to file>

		Linux (and Mac):
		openssl md5 <path to file>

		sha-1 checksums can be generated in a similar manner:

		CertUtil -hashfile <path to file>  sha1
		openssl md5 <path to file> sha1

		OpenSSL is also available for Windows, but is not installed by default.

		To do all of this in one step, switch to the top level directory of what you want to check (eg, the survey folder for a particular year) and run:

		find . -type f -name '*'  -exec openssl md5 {} \; > <path to output file.txt>

		eg:

		find . -type f -name ‘*’ -exec openssl md5 {} \; > /tmp/mylistofmd5sforsomesurvey.txt

		Then, when uploading the files to the EFT, include the file manifest.


		Statistics Canada *used* to produce a manifest for each survey, showing what was supposed to be there. For data files (the flat ones), they usually added something like this as well:

		----------------------
		Information for file: test.csv
		Number of lines: 101
		Maximum line length 47, minimum line length 26,  variable records
		———————————

		So you could check the integrity of the flat files, at least. 

* Data corruption: CIS 2018 — Jan 13, 2022:

		There's something very wrong with the flat ASCII file in the CIS 2018 release (ie, /MAD_PUMF_FMGD_DAM/Root/5200_CIS_ECR/2018/Data/RAW/CIS_2018.txt). More specifically, there's a problem with the last line of the file.

		All of the other lines are as you'd expect; a line length of 1189 for a flat ASCII file. The last line, however, consists of 744 characters plus 108065536 null characters.

		This explains why the text file is a gigantic 107 Mb in size.

* Also in the NTS 2020 — Jan 25, 2022: 

		The Person file appears OK, with the correct number of records.
		The Visit file has last record corrupted entirely. It has 49153 records, but it should have 83033 records according to the codebook.
		The Trips file appears way too short and has the last record *partially* corrupted. There's 12695 records, but there's supposed to be 39682 according to the codebook.

* A very recent example: GSS Cycle 30: November 8, 2022:
	There was a data release but no information given.
	The readme was unchanged. 
	All the files were replaced.

# Outline:

* Common data problems
	* timestamp changes
	* duplication of data
	* data file corruption
	* data verification
	* reproducibility
	* verifying the authenticity of dissemination

* Easy solution is to use software like damage
	* interface overview

* Use cases: go through the above list and show how damage could be used
	* My SPSS/Stata/R job fails when I try to load a file:
		* cf. Data corruption: CIS 2018 — Jan 13, 2022
		* Damage can tell you that one of the files is filled with null characters; ie, the file is corrupt.

	* Data files are too short
		* cf. NTS 2020 — Jan 25, 2022
		* The Visit file has last record corrupted entirely. It has 49153 records, but it should have 83033 records according to the codebook.
		* The Trips file appears way too short and has the last record *partially* corrupted. There's 12695 records, but there's supposed to be 39682 according to the codebook

	* There could be a problem with a download; something seems wrong
		* cf. CIS 2018 — Jan 13, 2022
		* Other university is reporting errors
		* UBC reports its file size + compares to material on DLI FTP site
		* They match, but the other institution's doesn't, so it's a download problem.

* Other considerations:
	*Line endings on different platforms are different
	*Linux and mac use a line feed ('\n')
	*Windows uses a line feed plus a carriage return ('\n\r')
	This means that each line, if converted from one format to another (which FTP can potentially do automatically), is one byte shorter or longer
	*Damage gives a Windows line ending warning for text files

* Encoding issues
	* Not all text files are created the same way.
	* Characters with diacritical marks require an *encoding*, and that can vary from platform to platform
	* Statcan sometimes uses Windows-1252, sometimes UTF-8. (Note: they should switch to using UTF-8)
	* What does this mean in practice?
		* The classic Labour Force Survey example: 

* The hammer
	* show how the use of damage *at the dissemination* stage could be used to reduce or eliminate almost all of these problems.
	* At this point, demonstrate the file output capability.
	* Using damage to compare the output of two damage files

* Denouement
	* Source code, software downloads

* Questions

-->

# Checking data integrity with the _Damage_ utility 


<div style="text-align: left; margin-top: 10%; margin-left: 10%; size: smaller">

Jeremy Buhler (jeremy.buhler@ubc.ca)   
_Data Librarian, University of British Columbia Library_

Paul Lesack (paul.lesack@ubc.ca)  
_Data/GIS analyst, University of British Columbia Library_
</div>

Note: 
Jeremy

Thanks, Sandra and Margaret, for introducing some data integrity concepts, including the all-important checksum. The second half of this presentation will introduce software called Damage that makes it easier to check files for integrity, especially statistical files like those we work with regularly in the DLI. 

---

## Outline

<div class="larger">
<br>

 - Introduction to the Damage tool
 - Damage for data checkers<!-- .element: class="fragment fade-up" -->
 - Damage for data distributors<!-- .element: class="fragment fade-up" -->

</div>

Note:
Jeremy

We'll start with an introduction to the _Damage_ tool, which generates file manifests that can help verify data integrity. _Damage_ is software developed at UBC Library by Paul Lesack. It was created initially for local UBC Library needs but we believe others in the DLI community will find it useful. With that in mind, after introducing _Damage_ our presentation will draw on DLI-specific examples to show how it could help both data checkers and data distributors.

I want to stress that our purpose in choosing DLI examples is to make this presentation as relevant as possible to this audience. We're not making a statement about the Statistics Canada Data Access Division, whose work we are grateful for. But as anyone who works with data can attest, file integrity issues eventually come around to bite everyone. Our hope is that the _Damage_ tool can make those bites less painful and the recovery more swift.

---

## Manifests and checksums
  
<br>
<div><!-- .element: class="fragment semi-fade-out" data-fragment-index="1"  -->
"A manifest file in computing is a file containing metadata for a group of accompanying files that are part of a set or coherent unit."

<small>_From Wikipedia, <https://en.wikipedia.org/wiki/Manifest_file>_</small>
</div>

A manifest with checksums allows files to be validated for integrity<!-- .element: class="fragment larger fade-up" data-fragment-index="1"  -->

Note:
Jeremy

Here's the requisite Wikipedia definition. We already heard about checksums from Sandra and Margaret; a manifest in our context is just a file with metadata about a group of accompanying files. A very simple manifest could be a text file with a list of filenames and their sizes, but I'd argue that any useful data manifest should include...

...checksums so that the end user can check not just the _presence_ of all the files that should have been included in a data download, but also their _integrity_. If the checksums of the downloaded files match the checksums in the manifest we can be sure that nothing was lost or corrupted in the download process.

---

Simple checksums for non-programmers?<!-- .element: class="fragment fade-out" data-fragment-index="1" -->

<div><!-- .element: class="fragment fade-in" data-fragment-index="1" -->

 ![Damage Image](Images/2022-11-22_Data_Integrity/DamageImage.png)

<div class="larger"> 
<span class="yellow">Da</span>ta <span class="yellow">Ma</span>nifest  <span class="yellow">Ge</span>nerator
</div>

__https://ubc-library-rc.github.io/fcheck/__

</div>

Note:
Jeremy

It's one thing to talk about generating checksums and adding them to a manifest file. For those of us who are non-programmers it's something else entirely to do it efficiently...

...that's where _Damage_ comes in. As its name suggests, _Damage_ is a data manifest generator. It's available as a command line tool for those who prefer that type of interface, but also as a GUI utility that can be installed on Windows, Mac, and Linux computers - even if you don't have administrative privileges on your workstation. 

Why "fcheck"? That's the name of the Python library. It's not quite as catchy a name, though.

---

## Sample _Damage_ manifest for two SPSS files

<br> 

<div style="width:60%; position: relative; float:left">

```r [1-11|1,7|2,8|3,9|4,10|5,11]
Archives\Data\SPSS\CIUS_2020_EN.sav
md5 checksum : bd2f98e2282c76d63d6d4c30f4e93d73
Encoding: WINDOWS-1252
Number of records: 17409
Columns: 1354 constant records

Data\SPSS\CIUS_PUMF_2020.sav
md5 checksum : bc385cd6b83653d396e027abe1599f8f
Encoding: WINDOWS-1252
Number of records: 17409
Columns: 1354 constant records
```
</div>


<div style="width:40%; position: relative; padding-top: 1em; float:right">

 - file path & name 
 - checksum
 - encoding
 - \# of records
 - \# of columns/variables

</div> 

Note:
Jeremy

Here's an illustration of what _Damage_ can do. What you see on the left is a file manifest generated by _Damage_ for two similar SPSS .sav files. There's a text block for each file with the 

- file path and name (very useful if you're creating a manifest with many files in nested directories)
- checksum (in this example we use md5 but _Damage_ can be configured to provide many other hash types)
- encoding (this is often UTF-8 but can also be specific to an operating system; depending on how you intend to use the file this can be a very important piece of information that's often hard to find). Encoding differences can cause text corruption and often lead to unusual, difficult to diagnose errors.
- number of records (_Damage_ has features designed for statistical package files; manifests for Stata, SAS, and SPSS files can include the number of records and...
- the number of columns or variables

This is not an exhaustive list of the _Damage_ manifest options but it's enough to give you a taste of what's possible. 

---

<section data-background-color="#FFA602">
<div style="margin-top: 20%">

# Introduction to the _Damage_ tool 

</div>
</section>

Note:
Paul

In the next few slides we'll provide an introduction to working with the _Damage_ tool

---

## An overview of _Damage_

<div>

![Damage Interface](Images/2022-11-22_Data_Integrity/DamageInterface.png)<!-- .element height="70%" width="70%" -->

<div style="position: fixed; left: 180px; bottom: 75px; height: 45px; width: 225px; border: 3px solid #FF8C00;" class="fragment fade-in-then-out" data-fragment-index=1>
</div>

<div style="position: fixed; left: 653px; bottom: 79px; height: 45px; width: 125px; border: 3px solid #FF8C00;" class="fragment fade-in-then-out" data-fragment-index=2>
</div>

</div>

<div style="position: fixed; width: 20%; left:90%; top: 20%; text-align:left" class="fragment fade-in-then-out" data-fragment-index="1">

**File section**
  
Add/remove files and folders

</div>

<div style="position: fixed; width: 20%; left:90%; top: 20%; text-align:left" class="fragment fade-in-then-out" data-fragment-index="2">

**Output section**

Generate the manifest

</div>

Note:
* Fairly straightforward interface
	* Buttons are also found in the menu
	* Use the buttons to add/remove the files you want analyzed
	* Then hit the "Generate Manifest" button

---

## But that's not what what I want
	
![Damage Interface](Images/2022-11-22_Data_Integrity/DamagePreferences.png)<!-- .element height="70%" width="70%" -->

Note:
Paul

The default output may not be what you want, but that's OK. Much like other applications,
you can customize the output using the preferences window. There are a variety of options:

1. Shorten the file path to the lowest common denominator
2. Skip the checking of statistical package files; ie, don't show the number of records and cases
3. You can recursively check an entire tree
	* Don't accidentally select your entire drive unless you have a lot of time on your hands
4. The hash type field is arguably the most important. If your data set comes with checksums, you will need to match the type (md5, sha256, etc) otherwise you won't be able to tell anything
5. Lastly, there's a variety of output formats, the most common of which are plain text and csv. JSON is also available, just in case.

---

## Generating the manifest 

![Damage manifested](Images/2022-11-22_Data_Integrity/DamageManifested.png)<!-- .element height="70%" width="70%" class="fragment" data-fragment-index="1"-->


Note:
Paul

* To check your files, just hit the Generate Manifest button
* Note that this can take a while, and if you have a large file you may get a spinning beachball, some sort of windows warning, etc, while the manifest generates
* The output is displayed in the window.
* Most commonly used formats are plain text and csv, depending on whether or not you are a wordprocessor or spreadsheet person

---
## Saving

![Damage menus](Images/2022-11-22_Data_Integrity/DamageMenus.png)<!-- .element class="fragment"-->

Note:
Paul
	
Like every other application, you can save your work. 

The usual hotkeys work, but you can also use the _Actions_ menu.

However, Damage is not intended to be an editor, so if you, for some reason, intend to make changes, you're probably better off opening the file in another application

In fact, you can only make changes using Damage in the text and JSON files.

Printing is rudimentary, because Damage is designed to create a file to go with your data, not to produce pretty printed output.

---

<section data-background-color="#FFA602">
<div style="margin-top: 20%">

# _Damage_ for **data checkers**

Note:

Paul

We'll shift now to some examples that illustrate how _Damage_ can help with data checking workflows 

</div>
</section>


---

<!-- ### OMGWTF -->

![inline filtered](Images/2022-11-22_Data_Integrity/caution.png)

`Downloaded: some_data_set_v2_2_3.zip`

Note: 
Paul

* Imagine you have `some_data_set` already. Lucky you! But it's been updated from the last time you saw it.
* Even this example is optimistic: it has version numbers!
* How do you know what, if anything, has changed?

---

## Common data problems

* timestamp changes<!-- .element: class="fragment" data-fragment-index="1" -->
* duplication of data<!-- .element: class="fragment" data-fragment-index="2" -->
* data file corruption<!-- .element: class="fragment" data-fragment-index="3" -->
* reproducibility<!-- .element: class="fragment" data-fragment-index="4" -->
* data verification<!-- .element: class="fragment" data-fragment-index="5" -->

Note:
Paul

Unfortunately, it's a rare data set that comes with perfect documentation.

* timestamp issues: Depending on how you downloaded the data and how it was packaged, timestamps change. They're not really a good indicator of the *contents* of files
* duplication of data: Damage can tell you if files are identical if two checksums are identical. Sometimes that's OK, as with a bunch of shapefiles that share the same projection - the projection files will likely all be identical. Sometimes that's not OK. Maybe two files are supposed to be different but they aren't.
* data file corruption. The file *structure* may not be what it's supposed to be.
* reproducibility: Those wishing to reproduce the analysis of others need to have the same inputs, otherwise reproduction is impossible
* verifying the authenticity of dissemination: Without ideal documentation, true verification may be impossible, but Damage output allows you to make informed judgements if you need to. 

Damage doesn't address all of these common data checking problems, but it provides easy access to information about file contents so you can spot and investigate potential issues and make informed decisions

In many (and ideally most) cases there won't be anything wrong at all, but even then _Damage_ can save you time by focusing your attention only on files that may have changed.

---

## Example #1: GSS Cycle 30

Revised product announced November 8, 2022

<div style="position: relative; clear:both; margin-bottom: 2em"></div>

![GSS Cycle 30 EFT directories](Images/2022-11-22_Data_Integrity/FilezillaGSS30.png)<!-- .element align="right" width="25%" height="25%" style="margin-left: 20px" class="fragment" data-fragment-index="2" -->

<br>

* The readme was unchanged<!-- .element: class="fragment fade-in-then-semi-out" data-fragment-index="1" --> 
* Original files were moved to an 'Archives' directory<!-- .element: class="fragment fade-in-then-semi-out" data-fragment-index="2" -->
* All data and documentation files were replaced<!-- .element: class="fragment fade-in-then-semi-out" data-fragment-index="3" -->


<div style="position: relative; clear:both; padding-top: 1em" class="yellow fragment" data-fragment-index="4">

Damage manifest revealed that of 47 replaced files, only 3 had changed

</div>

<div style="position: fixed; right: -10px; top: 210px; height: 105px; width: 220px; border: 5px solid #FF8C00;" class="fragment fade-in-then-out" data-fragment-index=2>
</div>

<div style="position: fixed; right: -10px; top: 315px; height: 55px; width: 220px; border: 5px solid #FF8C00;" class="fragment fade-in-then-out" data-fragment-index=3>
</div>

Note:
Paul

Take, for example, the recent DLI update to GSS Cycle 30 announced on the DLI list on November 8, 2022. There were no issues with the files distributed on the EFT server, but there was also nothing to indicate which files had changed...

...All the originally released files were moved to an 'Archives' directory, which is great because we can keep track of the old and new versions. In addition... 

...a complete new set of GSS Cycle 30 files was added to the top-level 'Data' and 'Documentation' folders. These represent the most up-to-date versions. The question is: how many of those new files are actually different than their counterparts in the 'Archives' directory? This isn't just a "nice to know" question, it has big workload implications at DLI institions that redistribute this data to researchers. Adding files to repositories like Odesi and Abacus involves adding metadata for each file - it's not as simple as copying over the new folder. The workload difference between updating 5 files and 50 is substantial, so it pays to to put some effort into identifying which files changed. As you might guess, a _Damage_ manifest with checksums for all relevant files can identify which have identical contents - even if their filenames or 'last modified' dates are different...

...as it turned out, of the 47 files in the 'revised product' only 3 were different from the originals. Knowing this made the update process in the Abacus data repository much less onerous than it might have been.

---

## A technical aside

`[x for x in newdata if x['md5'] in [y['md5'] for y in old_data]]`	

Note:
Paul

Now here comes the boring technical aside. Damge has outputs for both CSV and JSON. You may ask why.

* Both are easily machine readable, so it's very easy to use  R, Python or any other computer utility like a spreadsheet to compare file names/checksums/record lengths or whatever you need.
* This helps to identify changes and errors
* Damage can also identify encoding errors which can potentially cause problems between systems
 	* Most commonly, Windows-1252 vs UTF-8
* This tiny code snippet just shows a python sample checking for duplicates in two JSON dictionaries
* And, in the case of CSV, some people just like spreadsheets.
---

## I only use a terminal

`root@i_heart_data data% damage -o json cis_2018.txt > I_made_a_manifest.json`<!-- .element: class="fragment"-->

Note:
Paul

Damage is also available as a command line application for Mac, Linux and Windows, so you never have to leave your safe space.


---
## Example #2: CIUS 2020

Revised product announced November 8, 2022 

<br> 

<div style="width:50%; position: relative; float:right"><!-- .element: class="fragment" data-fragment-index="2" -->

```r [1,5,7,11]
Archives\Data\SPSS\CIUS_2020_EN.sav
md5 checksum : bd2f98e2282c76d63d6d4c30f4e93d73
Encoding: WINDOWS-1252
Number of records: 17409
Columns: 1354 constant records

Data\SPSS\CIUS_PUMF_2020.sav
md5 checksum : bc385cd6b83653d396e027abe1599f8f
Encoding: WINDOWS-1252
Number of records: 17409
Columns: 1354 constant records
```
</div>


<div style="width:50%; position: relative; padding-top: 1em; float:left">

* Note indicates 2 variables added<!-- .element: class="fragment fade-in-then-semi out" data-fragment-index="1" -->
* Damage shows no change in # of variables in .sav files<!-- .element: class="fragment fade-in-then-semi out" data-fragment-index="2" -->

</div> 

<div class="yellow fragment" style="position: relative; clear:both; padding-top: 1em" data-fragment-index="3" >

Review of all files shows ASCII file changed but syntax files did not 

</div>

Note: 
Jeremy

Our second example is also quite recent. Some of you may have seen my email to the DLI list about the November 8 release of a 'revised product' for the 2020 Canadian Internet Use Survey...

...A text file accompanying the release indicated two variables had been added to the PUMF: age group and population centre. It was not clear from the note whether all files in the new release had changed, or only a subset as we saw in the last example...

...A _Damage_ manifest answered that question but it raised another that suggested a potential problem: the number of variables or columns was the same in the Archived and new versions of the SPSS file, contradicting the release note...

...My point here is not to explain this difference but to point out how a relatively simple data verification step - creating a manifest with the _Damage_ tool - called attention to something I wasn't looking for and led to the discovery of a large data integrity problem.  


---

# Example #3: CIS 2018

Data corruption: January 13, 2022


> There's something very wrong with the flat ASCII file in the CIS 2018 release (CIS2018.txt). More specifically, there's a problem with the last line of the file.<!-- .element: class="fragment" style="text-align:left; font-size=smaller; float:left;" -->

An examination using Damage showed that the last line consists of 744 characters plus 108,065,536 null characters.<!--.element: style="float:left; text-align:left;" class="fragment"-->

Note:
Jeremy

Data corruption doesn't occur frequently, but it does happen sometimes.
 
...In this case there's no visual example as the file has been replaced.


...Having a look at this file shows the issue. This explains why the text file was a gigantic 107 Mb in size, and also why everything that depended on the content of this file didn't work either.

---

<section data-background-color="#FFA602">
<div style="margin-top: 20%">

# Damage for **data distributors** 

Note:
Paul

What if you're *distributing* data? Does Damage have any use?

</div>
</section>

---

## The value of a published manifest

Note:
Paul

Everything we've just seen was carried out by a data checker, or an end-user. However, the people that originally crafted the data set almost certainly went through a similar process in the act of creating the data set itself.

These days, hardly anyone works alone. If there are changes to data sets (ie, a version 2), the people distributing the data set won't necessarily be the same people who made it in the first place. A tool like Damage allows them to easily document changes internally.

But there's more. Creating a manifest file as part of the metadata allows *everyone* to document the provenance of the contents. If manifests specific to each data set are included with the data, everyone can confirm that the downloads match the originals.

If there's a manifest with each version of a data release, a changelog is automatically generated.

---

## A proposal for consideration

That the Data Access Division include manifests with checksums with the data products it distributes 

Note:

Jeremy

Data manifests with DLI data are not a new concept; they were common a few years ago and fell into disfavour.

A manifest doesn't have to be created by Damage; it's just one of innumerable tools that does this sort of thing. However, it does have a great benefit of beeing free and multiplatform. And the csv export would allow users, say, to add in extra columns with extra information such as detailed file descriptions, notes, etc.

One thing Damage does do that isn't very common is checking the rectangularity of common statistical packages like SAS and SPSS. As these are unsurprisingly very common at a national statistical agency, Damage can speed up workflow over other products.

---

## I forgot everything

 ![Damage Image](Images/2022-11-22_Data_Integrity/DamageImage.png)

* Python library and applications: <https://github.com/ubc-library-rc/fcheck>
* Documentation <https://ubc-library-rc.github.io/fcheck>
* Questions
	* /dev/null<!-- .element: class="fragment" data-fragment-index="1" -->
	* Github issues<!-- .element: class="fragment" data-fragment-index="2" --> <https://github.com/ubc-library-rc/fcheck/issues><!-- .element: class="fragment" data-fragment-index="2" -->
	* Email:<!-- .element: class="fragment" data-fragment-index="2" --> [paul.lesack@ubc.ca](mailto:paul.lesack@ubc.ca)<!--.element: class="fragment"data-fragment-index="2" --> 

Note:
Jeremy concludes 

