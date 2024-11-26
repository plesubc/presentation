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
https://revealjs.com/markdown/
https://revealjs.com/fragments/

Presenter notes begin with `Note:` up until the end of the slide, ie `---`

Images example

![Damage Interface](Images/2022-11-22_Data_Integrity/DamagePreferences.png)

Place something like this after a fragment, but add the missing dashes -:

<!- .element: class="fragment" data-fragment-index="1" ->
Note that each *element* needs this if using markdown, which is a massive pain
-->
<!-- Begin presentation -->

<span style="text-align:left">

# Dataverse utilities 

</span>

Note:

Land acknowledgement: 
The UBC Vancouver campus is located on the traditional, ancestral, and unceded territory of the xʷməθkʷəy̓əm (Musqueam) peoples.

This is a *very* brief introduction to dataverse_utils

It will cover only the two most commonly used tools that help simplify and speed up your workflow

---

## What is "dataverse_utils" ?<!-- .element: style="text-align:left" -->


<span style="text-align:left">

`pip install dataverse_utils`<!-- .element: class="fragment" data-fragment-index="1" -->

</span>


Note:

* A set of Python utilities for working with Dataverse
* Does not require any programming
* Barely requires a knowledge of Python
* Designed to be easy to install

* Python comes preinstalled on many operating systems and if you're working with data you probably have it already.

* The easiest way to install is to use `pip`, but you can install in any way you like

* It will install a bunch of **console** utilities, which means it's available from the command prompt, powershell or terminal of your choice. It runs on anything that uses Python, so you're not limited to Windows or Mac.

---

<span style="text-align:left">

## Now what?

Simplified file workflow<!-- .element: class="fragment fade-up" style="font-size:1.0em; text-align:left; line-height:1.1em"-->

Manifest generator<!-- .element: class="fragment fade-up" style="font-size:0.75em; text-align:left; line-height:0.3em"-->


Edit the TSV<!-- .element: class="fragment fade-up" style="font-size:0.75em; text-align:left; line-height:0.3em"-->


Upload with the TSV uploader<!-- .element: class="fragment fade-up" style="font-size:0.75em; text-align:left; line-height:0.3em"-->

</span>

Note:

There are two utilities that I use more than any other
Manifest generator which creates the metadata for the study
The uploader which, unsurprisingly, uploads the data

---

<span style="text-align:left">

## Make the manifest

<span class="fragment" style="text-align:left">

First, arrange your data the way you like it. For example: 

```
.
├── Command Files
│   └── sample_data.sps
├── Data
│   └── sample_data.tsv
└── Documentation
    └── README.md
```

</span><!-- .element: class="fragment" data-fragment-index="1" -->


<span class="fragment" style="text-align:left">

Then, run the manifest generator from the terminal:

```
dv_manifest_gen -r * -f yourfile.tsv
```

</span><!-- .element: class="fragment" data-fragment-index="2" -->

</span>

Note:
* Arrange your upload in the way you would want it to appear in Borealis
* This includes the tree, so feel free to create directories as required (Note: this doesn't enforce the (idiotic) Dataverse directory naming rules)
* Don't worry about zip files; they won't be unzipped. If you want them unzipped, unzip them
* Run the manifest generator to create a spreadsheet of your uploads.

---

<span style="text-align:left">

## Edit your spreadsheet

![visidata](Images/2024-06-20_dataverse_utils_sp/visidata.png)<!-- .element: class="fragment" data-fragment-index="1" height="400" -->


</span>

Note:

* Most (or all) of the file metadata is built into this spreadsheet
* The Dataverse/Borealis file paths are based on the local structure
* The in a shocking twist, the description goes into the "description" field
* Tags are separated by commas, unlike the columns in a TSV spreadsheet.
* To avoid leaving the terminal, consider using something like [Visidata](https://visidata.org)

---

<span style="text-align:left">

## Upload

`dv_upload_tsv -p doi:test/invalid -k yer_borealis_key  -u https://borealisdata.ca yourfile.tsv`<!-- .element: class="fragment" data-fragment-index="1" -->

</span>

Note:

* Run the terminal command using the TSV file that you just created

* You need an API key, because it uses the Borealis API (find this by clicking on your name, then "Create API token")

* Zip files will *not* be unzipped

* The uploads will pause while tabular files are being processed, because you can't add files while tabular files are being processed

    * So add them at the bottom if you remember

* You can also restrict files if required
* If you have 100 or 1000 files you can go for coffee or a martini

---

<span style="text-align:left">

## TLDR;


`pip install dataverse_utils`

**Documentation:** [ubc-library-rc.github.io/dataverse_utils)](https://ubc-library-rc.github.io/dataverse_utils)

**Source code:** [github.com/ubc-library-rc/dataverse_utils](https://github.com/ubc-library-rc/dataverse_utils)

**Visidata:** [visidata.org](https://visidata.org)

**Email:** [paul.lesack@ubc.ca](https://directory.library.ubc.ca/people/view/182)

</span>

Note:

There is much more to dataverse_utils than just these two things

While the tools are built for UBC, most of them will have some general utility

You can do things like copy records, bulk delete and release, migrate studies or use the code in your own projects

dataverse_utils is developed continually, if not continuously. There is an issues page on github where bug reports go for aging.
