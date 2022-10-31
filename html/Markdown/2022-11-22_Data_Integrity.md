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


# Title 
### Academic subtitle

## Authors etc. 
---
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

		This explains why the text file is a gigantic 107 Mb in sise.

* Also in the NTS 2020 — Jan 25, 2022: 

		The Person file appears OK, with the correct number of records.
		The Visit file has last record corrupted entirely. It has 49153 records, but it should have 83033 records according to the codebook.
		The Trips file appears way too short and has the last record *partially* corrupted. There's 12695 records, but there's supposed to be 39682 according to the codebook.


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

* Caveats:
	Line endings on different platforms

* The hammer
	* show how the use of damage *at the dissemination* stage could be used to reduce or eliminate almost all of these problems.
	* At this point, demonstrate the file output capability.
	* Using damage to compare the output of two damage files

* Denouement
	* Source code, software downloads

* Questions


