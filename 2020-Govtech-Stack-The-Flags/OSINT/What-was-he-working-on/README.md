# What is he working on? Some high value project?

## Description
```
The lead Smart Nation engineer is missing! He has not responded to our calls for 3 days and is suspected to be kidnapped! Can you find out some of the projects he has been working on? Perhaps this will give us some insights on why he was kidnapped…maybe some high-value projects! This is one of the latest work, maybe it serves as a good starting point to start hunting.

Flag is the repository name!

Developer's Portal - STACK the Flags

Note: Just this page only! Only stack-the-flags-2020 page have the clues to help you proceed. Please do not perform any scanning activities on www.developer.tech.gov.sg. This is not part of the challenge scope!
```

## Solution

Inspecting the source code of the website for comments yielded a few results, but this one was the most intriguing: a comment mentioning a [GitLab profile](https://gitlab.com/joshhky) `joshhky`.

![comment](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/What-was-he-working-on/comment.png)

Viewing the profile showed that he was working on some projects from the `KoroVax` team - an organisation that was mentioned in a few other challenges in the same CTF! However, inspecting all of the repositories didn't seem to yield anything that would be considered to be of "high value", and the `manuka` repository was indeed a self-referential honeypot.

![profile](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/What-was-he-working-on/gitlab.png)

After being stumped for a short while (...aaand purchasing a hint too), we found a reference to a seemingly non-existent repository in one of the commits made by `joshhky`. We then went to [the Internet Archive](https://archive.org) to view an archive of the Korovax team page, and found the same repository that was mentioned! Guessing from the name `krs-admin-portal`, that repository would most likely be for an administrative portal, certainly something of high value.

![reference](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/What-was-he-working-on/adminportal.png)

Putting that repository name as the flag turned out to indeed be correct!

## Flag

`govtech-csg{krs-admin-portal}`
