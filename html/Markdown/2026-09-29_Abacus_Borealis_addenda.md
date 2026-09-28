## Abacus dataset **not** held by Odesi

1996 Census Metropolitan Areas, Census Agglomerations and Census Tracts reference maps: individual maps

 <https://abacus.library.ubc.ca/dataset.xhtml?persistentId=hdl:11272.1/AB2/0SNKZP>


[Homicide Survey 1960 - 2020. Custom Tabulation]
<https://abacus.library.ubc.ca/dataset.xhtml?persistentId=hdl:11272.1/AB2/CWQQJF>

Notes:
The maps don't appear in Borealis at all; they were a special request from UBC.

Also things like custom tabulations which UBC ordered will not generally be present in Odesi unless Odesi harvested them.

---

## Abacus dataset held by Odesi, with no value-added files

Employment Dynamics, 1983-1999

* <https://abacus.library.ubc.ca/dataset.xhtml?persistentId=hdl:11272.1/AB2/W1XKKC>
* <https://borealisdata.ca/dataset.xhtml?persistentId=doi:10.5683/SP3/MJ06EP>

Files not in Odesi

```
abacus	hdl:11272.1/AB2/W1XKKC	Employment Dynamics, 1983-1999	GeneralProductInformation.pdf
abacus	hdl:11272.1/AB2/W1XKKC	Employment Dynamics, 1983-1999	LicenseAgreement.pdf
abacus	hdl:11272.1/AB2/W1XKKC	Employment Dynamics, 1983-1999	TableNotes.pdf
```

Notes:
For Employment dynamics, UBC just turned the notes into a PDF and the rest of it is already taken care of by the licence agreement.

---

## A more trivial example of no value added

Supply and Use and Input-Output Tables, 2020

* <https://abacus.library.ubc.ca/dataset.xhtml?persistentId=hdl:11272.1/AB2/MMKZFM>
* <https://borealisdata.ca/dataset.xhtml?persistentId=doi:10.5683/SP3/Z5DO3K>


`Input-Output-Tables-2020_FileManifest.txt`

Notes:
Statcan doesn't believe in manifests, but UBC does. But transferring the manifest would be dumb because we would have to manually check file names.

----

## Abacus dataset held by Odesi, but Abacus has additional files that are useful to Odesi

Census of Canada. Topic-based Tabulations. Basic Cross-tabulations, 2001 

<https://abacus.library.ubc.ca/dataset.xhtml?persistentId=hdl:11272.1/AB2/Y0PHTI>

Specifically:

<https://abacus.library.ubc.ca/file.xhtml?persistentId=hdl:11272.1/AB2/Y0PHTI/WSW0EU> cmpared to <https://borealisdata.ca/file.xhtml?fileId=29068&version=3.1>


Notes:

Borealis has a file with the same *name*, but with a different md5 and metadata which does not match the content of the IVT. In this case, there is a problem with the Borealis file.

----

## Edge cases

Is value added? This is a judgement call.

<https://abacus.library.ubc.ca/dataset.xhtml?hdl:11272.1/AB2/GKB6YG>
<https://borealisdata.ca/dataset.xhtml?persistentId=ddoi:10.5683/SP3/JKIHMG>

UBC has the *original* microdata from 1987

Notes:
Borealis' data file has been formatted differently. Presumably the contents are the same.
