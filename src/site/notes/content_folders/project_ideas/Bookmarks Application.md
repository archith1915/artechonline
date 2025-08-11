---
{"dg-publish":true,"permalink":"/content-folders/project-ideas/bookmarks-application/","dgShowToc":true}
---

# Feature list

## Overview

A web based application that can be used to save or bookmark links. Some example categories will be Technology, Designing, AIs, Products, Coding, Defence, Knowledge, English resources etc. Each link is assigned with a category and some tags like #foundOnInstagram, #fondOnInstagram etc. The user must be given an option to add links to the database with a short description, category, title and an AI (possibly) adds tags to it automatically which the user can edit if required. Further the user should also be able to search for links (items), retrieve or group links based on their tags etc.

Insertion, updation and deletion options should be given. An admin page should let the user track the count of links in each category and each tag, also add, edit, remove categories. 

The plan is to use a robust authentication with something known (no google login). Each user should be able to have his own data. For now, google sheets is to be used as our database. The admin page asks the user to enter his sheet link. Every user will create a copy of the template google sheet to his own account and paste the link in the admin page. The website will perform all the operations on that particular link.

Another field in the admin page asks the user to add a shared sheet link. The shared sheet will be shared among different users. Adding users who can access this shared sheet is not the concern of the website. 

The website will have separate pages for different categories, tags and groups. The 'Add link' form allows the user to add the link, title, description, tags and a checkbox decides whether the link should be shared with the group, if checked, it will be inserted to both the user's personal database as well as the group database. A column in the group database should store the name of the user who added the link and should provide edit and delete access to only that user (owner or creator). Rest of the users should only read the link. 

All the pages should have a search box, a filter to filter links based on the tags. Links are displayed as cards, with a open link button or icon, the date created, the date updated and the owner (only for group links page). The owner should be hidden if it is a personal database. On clicking on the card, a details page displays the title, link, description, preview, tags, creation and updation dates along with options to edit, delete and add to group options. Duplicate links in the group should be discarded if added multiple times even if added by different users.

An agentic AI should be able to summarize and return results through normal language (english) prompts. The entire database can be hosted as a csv and fed to the AI for training. Suggest me what can be done in this regard.


The frontend is to be built with a responsive framework like react.js, the backend is going to be express.js. For read operations, link of the sheet hosted as a csv file on to the web (using the native publish to web option on google sheet) will be used. For create, update and delete operations - google sheets API can be used. Options like share link, copy link (for each link) are to be included. Dark mode, custom theming should be included. Interactive react elements are to be included. The entire website will be vibe coded. So give me the complete roadmap, tech stack, supported fully-free hosting service, libraries (UI, AI, authorization) and everything that is needed.