# Dataverse at UBC Library

![](Images/2021-11-17_Dataverse_Panel/worker.png)

- Eugene Barsky and Paul Lesack, UBC Library
- November 2021

--- 

# Overview 

- Research data - Scholars Portal Dataverse 
    - Mediated deposits - Curation  - Allocation of Dataverses
- Licensed data - Abacus Dataverse
    - Authentication - Managing data - API use    
- dryad2dataverse platform
    - Harmonizing data holdings

 
---
# Research Data 
- UBC Library started to work on RDM in 2014
- First deposits were **fully** curated

Note:

---
# Research Data 
![inline](Images/2021-11-17_Dataverse_Panel/image1.jpg)


Note:

---
# Research Data 
- Hired a PhD student to do data curation
- Took a lot of time and resources, data dictionaries, recoding
- Data management vs. data curation


Note:

The student wasn't very good and I (Paul) had to a lot of the work. Peter Ward was before 2014

---
# Research Data 
![inline](Images/2021-11-17_Dataverse_Panel/image2.jpg)


Note:

---
# Research Data 
- Fast forward six years
- Mediated deposit
    - Users can login and deposit data
    - RDM Librarian / Analyst review deposits and consult with users to improve
    - Data is published


Note:

Did you want to mention DOIs here?

---
# Research Data 
- Curation
    - Every dataset needs **attention**
    - We haven't seen one that does not
    - Common issues: 
         * Lack of data dictionaries
         * Corrupt data files 
         * Insufficient metadata
         * No geospatial metadata
    

Note:

---
# Research Data

#### Data Curation, Level 2: <!-- .element: style="text-align: left;"  --> 

Activities that enhance the discoverability of datasets and help ensure their usability over time.<!-- .element: style="text-align: left;"  -->

Eg. recommended metadata fields are populated and dataset includes sufficient documentation to allow a user with a similar background to understand the dataset and open and use the files.<!-- .element: style="text-align: left;"  -->

Note:

---
# Research Data

![inline](Images/2021-11-17_Dataverse_Panel/image3.jpg)

An example of a metadata enhancement request

Note:

---
# Research Data
- We do allow (and encourage) some research groups to create and manage their own Dataverses
- Examples: 
    - Housing Research Collaborative (20 datasets)
    - Centre for Sustainable Food Systems (22 datasets)
    - Dr. Paul Pavlidis Dataverse (36 datasets)
    - Many more...


Note:


---

![inline](Images/2021-11-17_Dataverse_Panel/dryad2dataverseLogo.png)

---

# dryad2dataverse
- A platform agnostic tool which harvests material from Dryad
- Can be automated if required
- Requires zero researcher effort
- Associated python package can be used for other metadata conversions


Note:

dryad2dataverse is a metadata converter and harvester which extracts material from Dryad
<https://datadryad.org> and inserts it into a Dataverse installation (in this case Scholars Portal)

Requires no effort from researchers who have deposited information into Dryad, making the institutional partnership more valuable.

Python library can be used for easier metadata conversions. The Dryad data structure is easy, but Dataverse's JSON is complex. dryad2dataverse allows you to work with the easier structure.

--- 

# dryad2dataverse

* Metadata from Dryad is preserved as much as possible
* DOIs from Dryad are written into Dataverse records
* JSON metadata from Dryad is automatically inserted into a Dataverse record by default.

Note:

Nothing is perfect. Very large files can't be transferred and are flagged.

---
# dryad2dataverse

- No coding
- No dedicated server
- Minimal platform requirements
- Easy installation
    -  `pip install git+https://github.com/ubc-library-rc/dryad2dataverse.git@master`


Note:

If you hate coding, dryad2dataverse comes with a handy command line tool that requires nearly zero effort. No knowledge of Python is required

It doesn't require perpetual uptime, so a dedicated server isn't required

It will run on anything that supports Python 3.6 or greater. This includes things like cell phones, although that would not be a recommended platform.

---

# dryad2dataverse

- **Code** 
	- <https://github.com/ubc-library-rc/dryad2dataverse>
- **Documentation** 
	- <https://ubc-library-rc.github.io/dryad2dataverse/>


Note:

Not on PyPi. It may be somewhat *too* specialized for that.

---

![inline](Images/2021-11-17_Dataverse_Panel/abacus_logo.png)

---
# Licensed data

* UBC hosts a Dataverse installation which holds licensed (ie, commercial) data sets
* Multi-university consortium
* Common feel between two separate Dataverse installation platforms

---

# Licensed data

* Like Scholars Portal, users authenticate via Shibboleth
* Data sets that are not the product of the university research
* Data sets are organized by *license* 
* Participating institutions have their own dataverses

Note:

* The line between licensed data and research data can sometimes be fuzzy, but generally speaking we define licensed data as that which has not been created by a researcher to answer a specific research question.

* Organizing by license allows adding universities to Dataverses for which they have purchased a license. Data sets can then be restricted and only open to those institutions.

eg. DMTI Spatial Data

* Also allows open data with no restrictions, like the large Statistics Canada collection

* Note that administrative data (like campus orthophotos and lidar) are considered licensed data, not research data, as the data sets are usually for more general use

* Generally, material to which only one institution has access is placed in that institution's dataverse. Material to which more than one institution has access is placed in a dataverse that has multiple user groups assigned to it. Each university controls its own "personal" dataverse.

---
# Licensed data

* End user experience is nearly the same as for Scholars Portal
	* Most of the tool installed are the same
	* API access is available just as for research data

---

# Questions?


Eugene Barsky <!-- .element: style="text-align: left;"  -->   
*Head, University of British Columbia Library Research Commons*<!-- .element: style="text-align: left;"  -->   
eugene.barsky@ubc.ca<!-- .element: style="text-align: left;"  -->   


Paul Lesack<!-- .element: style="text-align: left;"  -->   
*Data/GIS Analyst*<!-- .element: style="text-align: left;"  -->   
paul.lesack@ubc.ca<!-- .element: style="text-align: left;"  -->   

Note:



