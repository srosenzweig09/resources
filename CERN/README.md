# CERN Resources

This page contains links to various resources that are relevant to CERN.

## Table of Contents

- [CERN Resources](#cern-resources)
  - [Table of Contents](#table-of-contents)
  - [CERN](#cern)
    - [Computing Tools](#computing-tools)
    - [CERN Discussion](#cern-discussion)
    - [GRID Certificates](#grid-certificates)
  - [LHC](#lhc)
  - [CMS](#cms)
    - [CMS Membership](#cms-membership)
    - [HyperNews](#hypernews)
    - [CMS Discussion](#cms-discussion)
    - [CMS Data Storage and Access](#cms-data-storage-and-access)


## CERN

### Computing Tools

- [CERN Account Management](https://account.cern.ch/account/) - Manage your computing accounts and service subscriptions
- [GRID Certificate](https://twiki.cern.ch/twiki/bin/view/CMSPublic/WorkBookStartingGrid#ObtainingCert) - CMS uses a globally distributed computing system for data analysis. A GRID certificate grants you access to this system.
- [Service for Web-based ANalysis (SWAN)](https://swan.web.cern.ch/swan/) - A platform to perform interactive data analysis in the cloud.
- [CERNBox](https://cernbox.web.cern.ch/cernbox/) - CERNBox provides 'cloud' data storage to anyone who has a standard CERN computing account. You can store your data, share it and synchronise it across devices.

### CERN Discussion

- [HyperNews](https://hypernews.cern.ch) - A collection of discussion groups related to each experiment at CERN.

### GRID Certificates

In order to access specific websites and use the HTC tools, each user must obtain a GRID certificate. Installation on a server for job submission is fairly straightforward. The only nuance I encountered is that it wouldn't install properly unless I provided a PEM password. The certificate itself does not **require** a password, but I couldn't install the certificate in Safari without password-protecting the certificate. So if you are having trouble getting the certificate to show in Safari, make sure it is password-protected when you import it into Keychain Access.

## LHC

- [LHC Schedule](https://lhc-commissioning.web.cern.ch/schedule/LHC-long-term.htm)

## CMS

### CMS Membership

- [CMS New Member Registration](https://cms.cern.ch/iCMS/jsp/secr/reg/regCMS.jsp) - Submission form to request CMS membership.
### HyperNews

### CMS Discussion

- [CMS HyperNews](https://hypernews.cern.ch/HyperNews/CMS/login.pl?&url=%2fHyperNews%2fCMS%2ftop%2epl) - A collection of discussion groups comprising the primary discussion tool in CMS
  > 1. Open a terminal
  > 2. Type `ssh yourcernusername@lxplus.cern.ch`
  > 3. Input your CERN account password when prompted
  > 4. Type `ssh hypernews.cern.ch`
  > 5. Fill in your details as requested
  > 6. Enter your user ID and password
  > 7. Click 'Subscribe to Forums'

### CMS Data Storage and Access

- [Data Aggregation System](https://cmsweb.cern.ch/das/) - DAS is an opensource virtual data service integration platform. The acronym DAS stands for Data Aggregation System. It provides a a common layer above various data services, allowing end users to query one (or more) of them with a more natural, search-engine-like interface. *Safari or Firefox recommended.*