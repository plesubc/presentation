## Abacus-to-Borealis migration
### Impact on Odesi
<br/>
<br/>

Jeremy Buhler, Data Librarian\
[jeremy.buhler@ubc.ca](mailto:jeremy.buhler@ubc.ca)<!-- .element: class="smaller" --> 

Paul Lesack, Data & GIS Analyst\
[paul.lesack@ubc.ca](mailto:paul.lesack@ubc.ca)<!-- .element: class="smaller" --> 

<https://plesubc.github.io/presentation/html/2026-09-29_Abacus_Borealis.html> <!-- .element: class="smaller" -->


Note: 

---

## About Abacus
### https://abacus.library.ubc.ca

- Open and licensed data repository <!-- .element: class="fragment" data-fragment-index="1"  -->
- Hosted by UBC <!-- .element: class="fragment" data-fragment-index="1" -->
- Partnership with SFU, UNBC, UVic <!-- .element: class="fragment" data-fragment-index="1" -->
- Includes StatCan and DLI data 


Note: 

---

## Migration goals

- Preserve access for Abacus users
- Minimuze disruption to Borealis/Odesi 

**Challenges:** avoid duplication, maintain record quality in Odesi 

Note: 


---

## Abacus collection groups

1. datasets that _do not_ belong in Odesi
    - licensed for UBC users
    - not in scope for Odesi collections
    - **Action:** migrate to UBC Borealis

2. geospatial datasets
    - DMTI, other geospatial data
    - **Action:** migrate after 2027 GeoPortal upgrade


3. datasets that duplicate or enhance Odesi
    - StatCan open data, DLI
    - **Action:** merge with Odesi collections


---

## Merge strategy: scenarios

These apply to DLI and StatCan datasets


---

## Scenario 1
Abacus dataset _not_ held by Odesi
---

<span style="text-align:left">

1996 Census Metropolitan Areas, Census Agglomerations and Census Tracts reference maps: individual maps

 <https://abacus.library.ubc.ca/dataset.xhtml?persistentId=hdl:11272.1/AB2/0SNKZP><!-- .element target="_blank" -->


[Homicide Survey 1960 - 2020. Custom Tabulation]

<https://abacus.library.ubc.ca/dataset.xhtml?persistentId=hdl:11272.1/AB2/CWQQJF><!-- .element target="_blank" -->

</span>

Note:

The maps don't appear in Borealis at all; they were a special request from UBC.

Also things like custom tabulations which UBC ordered will not generally be present in Odesi unless Odesi harvested them.

---


## Scenario 2

Abacus dataset held by Odesi, with no value-added files

---

## A trivial example of no value added

<span style="text-align:left">

Supply and Use and Input-Output Tables, 2020

* <https://abacus.library.ubc.ca/dataset.xhtml?persistentId=hdl:11272.1/AB2/MMKZFM><!-- .element target="_blank" -->
* <https://borealisdata.ca/dataset.xhtml?persistentId=doi:10.5683/SP3/Z5DO3K><!-- .element target="_blank" -->


`Input-Output-Tables-2020_FileManifest.txt`

</span>

Note:

Statcan doesn't believe in manifests, but UBC does. But transferring the manifest would be dumb because we would have to manually check file names.

---

## Less obvious, but still without value

<span style="text-align:left">

Employment Dynamics, 1983-1999

* <https://abacus.library.ubc.ca/dataset.xhtml?persistentId=hdl:11272.1/AB2/W1XKKC><!-- .element target="_blank" -->
* <https://borealisdata.ca/dataset.xhtml?persistentId=doi:10.5683/SP3/MJ06EP><!-- .element target="_blank" -->


Files not in Odesi

```
abacus	hdl:11272.1/AB2/W1XKKC	Employment Dynamics, 1983-1999	GeneralProductInformation.pdf
abacus	hdl:11272.1/AB2/W1XKKC	Employment Dynamics, 1983-1999	LicenseAgreement.pdf
abacus	hdl:11272.1/AB2/W1XKKC	Employment Dynamics, 1983-1999	TableNotes.pdf
```

Note:

For Employment dynamics, UBC just turned the notes into a PDF and the rest of it is already taken care of by the licence agreement.


---

## Scenario 3

Abacus dataset held by Odesi, but Abacus has additional files that are useful to Odesi

---

<span style="text-align:left">

Census of Canada. Topic-based Tabulations. Basic Cross-tabulations, 2001 

<https://abacus.library.ubc.ca/dataset.xhtml?persistentId=hdl:11272.1/AB2/Y0PHTI><!-- .element target="_blank" -->

Specifically:

<https://abacus.library.ubc.ca/file.xhtml?persistentId=hdl:11272.1/AB2/Y0PHTI/WSW0EU><!-- .element target="_blank" --> compared to <https://borealisdata.ca/file.xhtml?fileId=29068&version=3.1><!-- .element target="_blank" -->


Note:

Borealis has a file with the same *name*, but with a different md5 and metadata which does not match the content of the IVT. In this case, there is a problem with the Borealis file. So that's not great.

---

## Edge cases

<span style="text-align:left">

Is value added? This is a judgement call.

* <https://abacus.library.ubc.ca/dataset.xhtml?hdl:11272.1/AB2/GKB6YG><!-- .element target="_blank" -->
* <https://borealisdata.ca/dataset.xhtml?persistentId=ddoi:10.5683/SP3/JKIHMG><!-- .element target="_blank" -->

UBC has the *original* microdata from 1987
</span>
Note:

Borealis' data file has been formatted differently. Presumably the contents are the same.

---

## Impact on Odesi users

- "Abacus" option in search interface
- Search results may include datasets licensed only for UBC users

---


## Questions?

Jeremy Buhler, Data Librarian [jeremy.buhler@ubc.ca](mailto:jeremy.buhler@ubc.ca)\
Paul Lesack, Data/GIS Analyst [paul.lesack@ubc.ca](mailto:paul.lesack@ubc.ca)

