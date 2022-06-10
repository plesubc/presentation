autoscale: true
slidenumbers: true


## Research Data Management -- Introduction for ICORD
- Eugene Barsky and Paul Lesack
- UBC Library, May 2022
    - [eugene.barsky@ubc.ca](mailto:eugene.barsky@ubc.ca)
    - [paul.lesack@ubc.ca](mailto:paul.lesack@ubc.ca )
- [https://researchdata.library.ubc.ca](https://researchdata.library.ubc.ca/)

---
![right fit filtered](ubc_street_signs.jpg)
## I acknowledge
I am grateful to the Musqueam people on whose unceded land I work, live and walk every day


---


## Agenda
- Define Research Data
- Research Data & The Data Life Cycle
- Data Management Plans
- Organizing Data: File Naming, README’s & Metadata
- Storing & Protecting Research Data
- Data Repositories

---

## What is data

![inline filtered](data-cake-01.jpeg)

---

## What is Research Data
- Facts, measurements, observations, recordings, or records, produced during a research project. 
     - Made of many file types, most disciplines have common types:  Notes, spreasheets, images, designs, algorithms, diagrams, data files, etc. 

---

![ right fit filtered](research_data_lifecycle.jpg)
## Research Data Lifecycle
- Start working with data with an end in-mind

---

## What is Research Data Management
- Processes applied throughout the lifecycle of a research project to guide the collection, documentation, storage, sharing, and preservation of research data.
    - [Portage Network RDM Primer](https://portagenetwork.ca/wp-content/uploads/2019/08/Primer_RDM_August2019_EN.pdf), 2019

---

## Why Prioritize Research Data Management (RDM)?
- RDM helps organize your research data before, during, and after your research cycle. 

- Makes responsibilities clear within research team & during team transitions


---

![right fit filtered](tri-agencies_funding.jpg)
## Tri-Agency Funding Requires RDM
-As soon as Spring 2022, some Tri-Agency grants will require _Research Data Management Plans_ in the application package. 


---

##Good RDM Looks Like:
- Clear distribution of team RDM responsibilities 
- Accurate metadata about each research data file and variable
- A system for data storage, security, and backup
- Plan for data sharing, repository selection, and licensing for reuse
- Uniform and functional standards for naming and organizing data

---

## Good RDM Looks Like:
- My favourite example: Elizabeth Wolkovich's [Lab Manual](https://github.com/temporalecologylab/labgit/blob/master/datacodemgmt/tempeco_DMP.pdf) 

---

## FAIR Data is good data
![inline filtered](FAIRdataprinciples_foster.png)

---

## From Here
![inline filtered](messy.jpeg)

---

# to Here
![inline filtered](ordered.jpeg)

---

## Practical Tips (#1) -- Get yourself an ORCID iD
- An ORCID iD is a free, persistent identifier (PID) that you can connect to your published research, including datasets.
- Like a DOI but for you across your entire career
- It makes it easy to gather your attributions, grants, positions, and more in one place
- Register for your ORCID iD here: [https://orcid.org/](https://orcid.org/)

---

![ right fit filtered](research_data_lifecycle.jpg)

#Plan
---

## The Data Management Plan (DMP)
- Sets out how you will organize, store and share your research data at each stage in your project and after its conclusion.
- Incoming standard for funding agencies to require these in your grant applications.
    - [Tri-Agency Research Data Management Policy](http://www.science.gc.ca/eic/site/063.nsf/eng/h_97610.html) 


---
## You are not alone
### Data Management Plan (DMP) Assistant by Portage
- Free and Bilingual - [DMP Assistant] (https://assistant.portagenetwork.ca/)
- Provides templates tailored to various disciplines
- UBC has custom templates for our researchers
- Templates guide the structure and creation of DMPs, focusing in on what’s most important

---

## DMP Assistant
![inline filtered](dmp_assistant.jpg)

---

## DMP Exemplars 
- Portage offers examples of completed DMPs. 
- [Exemplars] (https://portagenetwork.ca/tools-and-resources/training-resources/?cn-reloaded=1) - different disciplines
   
---

## Practical Tips (#2)
-  Plan first

---

![ right fit filtered](research_data_lifecycle.jpg)
## Collect

---

## Data Collection
### Stop problems before they start
- Create a meaningful, organized system of variable names, file names, file structures
- Develop a directory structure (project, sample, etc.)
- Standardize your file naming system 

---

## Data Collection
- Document and share your process
- Write a comprehensive **readme.txt** outlining your variable names, applications, and notes that make the project replicable

---

![fit right filtered](file_names.png)
## Data Collection: File Naming
- Aim for concise but descriptive file names, a consistent naming system, and a simple hierarchy.

- UBC Guide for [File Naming](https://mfr.ca-1.osf.io/render?url=https://osf.io/pfweq/?direct%26mode=render%26action=download%26mode=render)


---

## Elements That Could Appear in a File Name
- Date of creation in ISO Standard YYYYMMDD format
- Name, initials or ID of the research group, institutional affiliation, editor, researcher
- A project name or code
- Short description of contents
- Location that produced the data
- Version number
- Format of the file, commonly seen as a file extension

---

## File Name Examples from Simple to Complex
- A presentation that two people are working on:
    - ShortDescription_Editor_YearVersion
    - RDMWebinar_NR_2021V02
- Meeting notes for a group that meets regularly:
    - YYYYMMDD_Group_Description
    - 20200318_RSpT_MeetingNotes
- Tree points in standardized geographic areas in shapefile format
    - Point_WesternRedCedar_BCGS092G032_20210719_shp.zip

---
## Practical Tips (#3) 
- Long, descriptive file names are better than short, confusing names, even if they take a long time to type

---

![ right fit filtered](research_data_lifecycle.jpg)
#Analyze

---


## Processing Your Data
- This can be iterative, in part or in entirety
- Keep an untouched, raw version of your data that is never changed. 
- A DMP will ask you to consider where and how data is stored & backed up.
- **Your code is also data**

---

## Data Storage: The Crucial Importance of Redundant Systems
- 3-2-1 backup rule: 
    - Have at least 3 copies of your data
    - The here copy, your working copy
    - The near copy on a backup disk. 
    - The far copy that can be accessed remotely.
    - Store the copies on 2 different media 
    - Keep 1 backup copy offsite

---
![right fit filtered](harddisk.jpg)
## Data Storage
- How often shall I back up data?
    - As often as you edit your data, you should update your backups. 
    - Personally I use [FreeFileSync](https://freefilesync.org/) to sync in real time

---

![](https://www.youtube.com/watch?v=8dhp_20j0Ys)

---

## UBC Storage Resources
- UBC-IT
    - [EduCloud Server Service](https://it.ubc.ca/services/web-servers-storage/educloud-server-service) - cost associated, need IT skills
    - [Teamshare](https://it.ubc.ca/services/web-servers-storage/teamshare-storage-service) - Internal fileshare, costs per GB per year
    - [OneDrive](https://it.ubc.ca/services/web-servers-storage/microsoft-onedrive) - 1TB of storage per user
    - [Home Drive] (https://it.ubc.ca/services/web-servers-storage/home-drive-storage-service)- personal storage only
    - [SharePoint](https://it.ubc.ca/services/web-servers-storage/sharepoint-software-service) - powerful, but complicated to develop

---

## UBC Storage Resources
- UBC ARC
    - [Chinook](https://arc.ubc.ca/chinook) - Object storage application

---

## UBC Storage Resources
- Compute Canada
    - [NetCloud](https://docs.computecanada.ca/wiki/Nextcloud) - 100Gb free per user, similar to Dropbox
    - [System storage](https://docs.computecanada.ca/wiki/Storage_and_file_management) - linux based for supporting high performance computing (HPC) analysis - up to 10Tb per research group.

---

## UBC Storage Resources
- UBC Online Storage Solutions [Comparison Chart](https://it.ubc.ca/sites/it.ubc.ca/files/UBC%20Online%20Storage%20Solutions%20-%20Features%20Comparison%20Chart.pdf)

---

## Storage Intricacies
- Is it FIPPA compliant?
    - For Faculty & Staff: Campus Home Drives, TeamShare, Chinook, OneDrive, EduCloud
    - For Students: OneDrive
- Is any of your data is sensitive? Does it contain identifying information?

---

## Storage Intricacies
- Is it free?
    - Yes: Home Drives up to 20GB, OneDrive, Chinook
    - No: Team Share, EduCloud, SharePoint

---

## Practical Tips (#4) 
- Backup your data. A lot.

---

![right fit filtered](metadata1.jpg)
## What is Metadata? - Data About Data
- Metadata is descriptive data regarding a dataset, a study, a collection of files, and variables.
- Metadata answers questions like:
    - Who?
    - What?
    - When?
    - Where?
    - Why?
    - How?

---
## Metadata isn't necessarily for you

- As a researcher, you know what your data shows
- Metadata is for someone else, or for you in six months/20 years

---

![right fit filtered](findable.jpg)

## Types of Metadata
- _Descriptive_: content and context of your data at both the dataset level and data file level.
    - Title, Author, Methods, Sponsors 


---

## Types of Metadata
- _Administrative:_ information needed to use the data.
    - Software requirements, copyright

- _Structural:_ how different data files relate to one another.
    - Information about the relationship between data files in a data set, file formats, variables

---


![fit right filtered](metadata_sticks.jpg)
## Data Documentation & README Files

- README.txt files are the most basic tool for project documentation.

- Plain text (.txt) files that contain basic descriptive metadata about your project.

---

## Data Documentation & README.txt Files

- README files accompany your data files throughout their life. 

- [UBC best practices for README files document](https://osf.io/aqxw3/)

---

## Content of README Files

- Contact information for researchers
- Description of dataset & date of collection
- Use license for your data
- Methods & instruments used in the collection & processing of your data
- File structure and relations for the data set
- Explanations of codes,  classifications, variables, and file names

---

![fit filtered](readmefile.png)



---

![fit filtered](data_dictionary.png)

---

![fit right filtered](data_variables.png)
##Not Everybody Knows...
- Define all jargon, “common knowledge,” and abbreviations
- Your data and README.txt files may be utilized by researchers outside of your field of study who may not have the same understandings
- Knowledge changes over time, don’t take understandings for granted

---

## Practical Tips (#5) 
- Write your documentation so that you have a self-contained data package for a non-specialist.

---

![ right fit filtered](research_data_lifecycle.jpg)
# Share and Preserve

---

## Share & Preserve Your Data for Reuse
- Much easier when you’ve maintained your RDM and implemented your DMP
- Effectively boxing up some of your research data
- All documentation and metadata should be complete at this stage

---

![fit right filtered](interoperable.png)
## Share & Preserve Your Data for Reuse
- May require converting to stable file-formats instead of proprietary formats
    - Tabular data as .CSV/.TSV, text files as .TXT or .PDF, etc.

---

## Long-Term Storage Considerations

- Where do you plan to hold the data long term?
- What forms of the data are you sharing?
    - Raw, processed, analyzed, and final are all options
    - Do the funding agency or publisher mandate any of these for you?


---

![fit right filtered](reusable.png)
## Long-Term Storage Considerations
- What license do you plan to apply? 
- Personally I like the [CC-0](https://creativecommons.org/share-your-work/public-domain/cc0/) and [CC-BY](https://creativecommons.org/licenses/by/2.0/) for research data 

---

## Practical Tips (#6) 
- Data licenses aren't optional. Pick one which meets the needs of you and your intended audience

---

![fit right filtered](open_data.png)
## Data Repositories
- Benefits of a repository: 
    - Persistent, unique identifier, e.g. DOI 
    - Backup and preservation 
    - Data citation 
    - License 
    - Version control 
    - Data integrity checks 

---

## UBC Repositories
- [UBC Dataverse Collection](https://researchdata.library.ubc.ca/deposit/dataverse) – An open source application to publish, share, reference, cite, extract and analyze research data. (Preferred) 

- [FRDR](https://researchdata.library.ubc.ca/deposit/frdr/) – The Federated Research Data Repository, is a Canadian national research data repository. 

- [Dryad](https://researchdata.library.ubc.ca/deposit/dryad/) – Dryad is an international, multi-disciplinary data repository that supports access to data underlying published literature. UBC is a Dryad institutional partner.


---

##UBC Repositories
- [Where Should I Deposit My Data – Quick Guide](https://mfr.ca-1.osf.io/render?url=https://osf.io/rc7de/?direct%26mode=render%26action=download%26mode=render)

---

## UBC Dataverse Collection
- UBC CWL integration
- Collaboration among Canadian institutions
    - Data is stored in Canada
- Limits individual files to 3 GB each but accepts all data formats
- Mints DOIs for datasets
- Discovery by Google, Summon, FRDR, DataCite

---

## Dryad
- UBC CWL integration.  
- Data curation review 
- Digital Object Identifiers (DOIs) at the dataset level. 
- No fees for basic data deposits - UBC Library is an institutional member
- If your files are <3GB, your data set goes into Dataverse anyway
- [Guides and instructions](https://researchdata.library.ubc.ca/deposit/dryad/)

---

## FRDR
- Data curation review 
- Digital Object Identifiers (DOIs) at the dataset level. 
- No fees for basic data deposits - UBC Library is an institutional member
- [Guides and instructions](https://researchdata.library.ubc.ca/deposit/dryad/)
- Support for large files

---

## The circle of repositories

- FRDR harvests from Dataverse
- Dataverse harvests from Dryad

---
## How to choose

For most purposes, Dataverse is a good choice

- Version control and persistent identifiers
- Obvious UBC branding
- Can (optionally) have collections by
    - organization (ie, ICORD)
    - PI/Lab


---

## Challenges to Depositing, Sharing Reusing Data
- Lack of metadata 
    - Include sufficient metadata (see tip #5)

- Proprietary, obsolete file formats 
    - Use preservation-friendly, open file formats

- Copyright, intellectual property rights unclear - No license
    - Encourage open access to data 

- Privacy, ethical concerns 
    - Obtain consent for data sharing and secondary use of data 
    - Check with Research Ethics Boards 

---

## RDM People at UBC

- Research Data Services Librarian, Eugene Barsky
- Paul Lesack, Data/GIS analyst 
    - [research.data@ubc.ca](mailto:research.data@ubc.ca)

- [UBC Library’s Research Data Management Site](https://researchdata.library.ubc.ca/)

- [Advanced Research Computing (ARC) at UBC](https://arc.ubc.ca/)

- [Research Commons Consultations & Workshops](https://researchcommons.library.ubc.ca/)

---

## RDM Guides at UBC
- [UBC Library Data Guide](https://mfr.ca-1.osf.io/render?url=https://osf.io/yujkv/?direct%26mode=render%26action=download%26mode=render)
- [Good Enough Research Data Management – A Very Brief Guide](https://mfr.ca-1.osf.io/render?url=https://osf.io/zjpqx/?direct%26mode=render%26action=download%26mode=render)
- [File Naming Guidelines](https://mfr.ca-1.osf.io/render?url=https://osf.io/pfweq/?direct%26mode=render%26action=download%26mode=render)
- [Creating A README For Your Dataset](https://mfr.ca-1.osf.io/render?url=https://osf.io/aqxw3/?direct%26mode=render%26action=download%26mode=render)


---

## Upcoming RDM Workshops by UBC Library
- UBC Library [Research Commons](https://researchcommons.library.ubc.ca/) hosts workshops on topics like citation management tools, systematic reviews, metadata, GitHub, R, NVivo, and more.
    - Upcoming [Research Commons Workshops](https://libcal.library.ubc.ca/calendar/vancouver?cid=7544&t=g&d=0000-00-00&cal=7544&ct=33914&inc=0)


---

#Thank you for joining us! 

- [research.data@ubc.ca](mailto:research.data@ubc.ca)
- [eugene.barsky@ubc.ca](mailto:eugene.barsky@ubc.ca)
- [paul.lesack@ubc.ca](mailto:paul.lesack@ubc.ca)

---

##Image Credits

- Slide 15 - [OpenAIRE](https://www.openaire.eu/how-to-make-your-data-fair)
- Slide 16, 17 - [Unsplash] (https://unsplash.com/@cleversparkle?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)
- Slide 28 - [XKCD] (https://xkcd.com/1459/)
- Slide 37 - [Flickr](https://www.flickr.com/photos/hi-phi/14699924741)
- Slide 47 - [Flickr](https://www.flickr.com/photos/centralasian/8071729256/in/photolist-digHTN-avThpo-2kGqoYg-2kLTv88-2kLTv71-2kLTv7M-2kLPHXg-2kGqoYv-2kLTWDu-2kGqnSY-2kGqn1Y-2kGqoXz-2kLTVvT-2kLPKDh-2kLTt7Q-2kGqm6S-2kLPKCR-2kLPKBP-2kLPKC5-2kGqnVz-2kLTtX7-2kGqnSs-2kLTt7j-2kGqmWv-2kGqm6m-2kLPHXw-2kGqn1x-2kLPJJr-2kLTUA1-2kLPJHj-2kLTTGs-2kGqm48-2kLTTFf-2kLTTF5)
- Slide 50 - [Flickr](https://www.flickr.com/photos/wakingtiger/)
