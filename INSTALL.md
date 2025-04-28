
# LedgerSMB Install

This doc is initially for keeping my personal notes regarding an eventual install document for LedgerSMB. Comments are welcome either as issues in the git repository or on matrix.

## Overview

This document is completely replaced by the instructions at [https://get.ledgersmb.org](https://get.ledgersmb.org)

My writing style is to just start writing ideas no matter how imperfect, thanks to my writing professor getting me over my hesitation to write. I say this because some people instinctively write finished prose. I don't. This document will get a lot of rewrites before it is ready for consideration. So there is no need to comment on grammar.  

Some of the content here may be copied from others and the LedgerSMB web site, all of course used by permission. If an acknowledgement is missed just let me know, it is not intentional.

Until this document is accepted into the main LedgerSMB repository it is completely unsupported. For supported install instructions see the LedgerSMB website at [https://ledgersmb.org/](https://ledgersmb.org/)

## The Future Structure

This Install document should be included with the distribution and not in a Wiki.  The problem with a Wiki is knowing if it is update to date with the distribution, or if has been left behind.  It should be the responsibility of the release process to make sure the Install document is up to date.

It was not clear to me if this document should be LaTeX or Markdown. I choose Markdown because I think there is a better chance that it will be kept up to date by more people. With that said, I prefer to write in LaTeX and would be happy to convert it. What I hate about Markdown for this use is no index and manually maintaining any internal links.

Eventually, when this document is accepted into the LedgerSMB repository I see replacing some of the Wiki content, removing some of the Wiki content, and/or auto publishing this doc to the Wiki. Of course up for discussion.

## The Guts For New Installs Only
There are 3 main components to LedgerSMB that are important components of the installation:

1. Web Server - which provides the interface to the user
2. LedgerSMB - which provides the business logic and connects the web server to the database
3. Database - which provides persistent storage

LedgerSMB makes available docker images for all 3 of these components. These docker images can be used as starting examples or used exactly as provided.

There are multiple ways to install LedgerSMB:

2. __Recommended Evaluation__ - Single Docker image for all 3 LedgerSMB components, simple security or no security  

   The security goal is nonexistent. This is meant for evaluation purposes on a single computer with easy set-up.  Targets a specific release.  Is not meant to contain any confidential data.

1. __Recommended Production on WAN__ - Docker images for all 3 LedgerSMB components, robust base security install

   The security goal is to protect LedgerSMB from internet wide attacks. As such, all communications between the web browser and web server will use industry standard https and public certificates set up by Let's Encrypt.  This requires a public domain name.  Port 80 (http) will be disabled.
   
   This will be a simple installation where all 3 docker images run on the same hardware. Running any of the docker images on their own hardware is an exercise for the installer.

   The docker network between the web server and database will not be accessible outside of the host. As such, no security is required.
   
   Targets a specific release.
      
2. __Recommended Production on LAN__ - Docker images for all 3 LedgerSMB components, self-signed certs  

   The security goal is to protect LedgerSMB from internal network monitoring. As such, the web server will be set up with self-signed certificates and each browser must be configured to accept the self-signed certificates.
   
   This will be a simple installation where all 3 docker images run on the same hardware. Running any of the docker images on their own hardware is an exercise for the installer.

   The docker network between the web server and database will not accessible outside of the host. As such, no security is required.
   
   Targets a specific release. This might just be a variation of the WAN install.
      
2. __Traditional__ - No Docker, installed directly in the hardware OS

   The security goal is completely up to the installer. This option provides the most freedom during install. The Install instructions are example guidelines only and will cover prerequisites and not security. The example install will target a specific release.
   
3. __Development__ - Docker for all 3 LedgerSMB components with git

   The security goal is nonexistent. This option provides the fastest way to develop and test various aspects of LedgerSMB using git as the source instead of a release.  The web server may not be production ready. The target is completely up to the installer.
   
4. __Combinations__ - Installing one or more LedgerSMB components directly in the hardware operating system and one or more LedgerSMB components as docker images

   Due to complexity, installing using combinations of docker and bare OS installation are not covered in the LedgerSMB Install instruction.

## Notes to myself

Need to incorporate [gwhitney's experience](https://github.com/ledgersmb/LedgerSMB/issues/4655#issuecomment-647317453)

Current Development Install Instructions

[Wiki 2017](https://ledgersmb.org/content/using-docker-develop-ledgersmb)

[Github](https://github.com/ledgersmb/ledgersmb-dev-docker)

Current Release Install Instructions

[Release Docker](https://github.com/ledgersmb/ledgersmb-docker)

[1.9.5 Readme](https://github.com/ledgersmb/LedgerSMB/blob/1.9.5/README.md)

