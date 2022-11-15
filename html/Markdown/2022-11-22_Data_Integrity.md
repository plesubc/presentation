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
# How to damage your data
## not destroy it

* Jeremy Buhler (jeremy.buhler@ubc.ca)  
	Data Librarian, University of British Columbia Library
* Paul Lesack (paul.lesack@ubc.ca)  
	Data/GIS analyst, University of British Columbia Library

---

You have downloaded some data

---

### OMGWTF

![inline filtered](Images/2022-11-22_Data_Integrity/caution.png)

`Downloaded: some_data_set_v2_2_3.zip`

Note: 

* Imagine you have `some_data_set` already. Lucky you! It has an update
* Even this example is optimistic: it has version numbers!
* How do you know what, if anything, has changed?

---

## Common data problems

* timestamp changes<!-- .element: class="fragment" data-fragment-index="1" -->
* duplication of data<!-- .element: class="fragment" data-fragment-index="2" -->
* data file corruption<!-- .element: class="fragment" data-fragment-index="3" -->
* data verification<!-- .element: class="fragment" data-fragment-index="4" -->
* reproducibility<!-- .element: class="fragment" data-fragment-index="5" -->
* verifying the authenticity of dissemination<!-- .element: class="fragment" data-fragment-index="7" -->

Note:
	Unfortunately, it's a rare data set that comes with perfect documentation. And even *with* perfect documentation, there can still be problems.
	For example (the list above)

---

## I don't want to be a programmer

 ![Damage Image](Images/2022-11-22_Data_Integrity/DamageImage.png)<!-- .element: class="fragment" data-fragment-index="1" -->

Data Manifest Generator<!-- .element: class="fragment" data-fragment-index="2" -->


Note:
	* There are many solutions to solving these problems, but almost all of them involve specialized knowledge
	* If only there were a tool you could download that can help with this sort of thing
	* Damage stands for Data Manifest Generator.
	* It could have been YACA for Yet Another Clever Acronym.

---

## An overview of Damage

![Damage Interface](Images/2022-11-22_Data_Integrity/DamageInterface.png)<!-- .element height="70%" width="70%" -->

Note:
	* Fairly straightforward interface
	* Buttons are also found in the menu
	* Use the buttons to add/remove the files you want analyzed
	* Then hit the "Generate Manifest" button

---

## But that's not what what I want
	
![Damage Interface](Images/2022-11-22_Data_Integrity/DamagePreferences.png)<!-- .element height="70%" width="70%" -->

Note:
* Can customize the output using the preferences
	1. Shorten path to the lowest common denominator
	2. Skip the checking of statistical package files
	3. Recursively checking an entire tree
		* Don't accidentally select your entire drive unless you have a lot of time on your hands
	4. The hash type ensures that the correct checksum is used. If your data set documentation comes with checksums in sha-256 format, this is where you select that option so that you can compare
	5. And a variety of output formats, the most common of which are plain text and csv. JSON is also available, just in case.

---

## Damaging your files

![Damage manifested](Images/2022-11-22_Data_Integrity/DamageManifested.png)<!-- .element height="70%" width="70%" class="fragment" data-fragment-index="1"-->

One touch checking


Note:

	* To check your files, just hit the Generate Manifest button
	* Note that this can take a while, and if you have a large file you may get a spinning beachball, some sort of windows warning, etc, while the manifest generates
	* The output is displayed in the window.
	* Most commonly used formats are plain text and csv, depending on whether or not you are a wordprocessor or spreadsheet person

---
## Saving

* Not rocket science

![Damage menus](Images/2022-11-22_Data_Integrity/DamageMenus.png)<!-- .element class="fragment" data-fragment-index="1"-->

Note:
	
Like every other application, you can save your work. However, Damage is not intended to be an editor, so if you, for some reason, intend to make changes, you're probably better off opening the file in another application

In fact, you can only make changes using Damage in the text and JSON files.

Printing is rudimentary, because Damage is designed to create a file to go with your data, not to produce pretty printed output.

---

# So what?

Use cases<!-- .element class="fragment" data-fragment-index="1"-->

---
# A simple example

* A very recent example: GSS Cycle 30: November 8, 2022:
	There was a data release but no information given.
	The readme was unchanged. 
	All the files were replaced.

---

# A more complex example

* CIUS 2020

---

# A  data corruption example

* Data corruption: CIS 2018 — Jan 13, 2022:

There's something very wrong with the flat ASCII file in the CIS 2018 release (ie, /MAD_PUMF_FMGD_DAM/Root/5200_CIS_ECR/2018/Data/RAW/CIS_2018.txt). More specifically, there's a problem with the last line of the file.

All of the other lines are as you'd expect; a line length of 1189 for a flat ASCII file. The last line, however, consists of 744 characters plus 108065536 null characters.

This explains why the text file is a gigantic 107 Mb in size.

---

# A technical aside

`[x for x in a if x['md5'] in [y['md5'] for y in dmg_data]]`	

Note:
	This is where the CSV and JSON outputs work ease of comparison
	* Both are easily machine readable, so it's very easy to use spreadsheets, R, Python or any other computer utility to compare file names/checksums/record lengths or whatever you need.
	* This helps to identify changes and errors
	* Damage can also identify encoding errors which can potentially cause problems between systems
	 	* Most commonly, Windows-1252 vs UTF-8

---

# All of this is fine

but. . . <!-- .element class="fragment" data-fragment-index="1"-->

life would be easier if a manifest was included with every data package.<!-- .element class="fragment" data-fragment-index="2"-->

Note: 
	All of the examples above show the use of Damage *where there is no current manifest*.
	Many of these problems can be discovered faster.
	* Running damage before dissemination can discover those errors before they are propagated to the world
	* Including a manifest created by Damage allows people downloading the data compare Damage manifests

	
