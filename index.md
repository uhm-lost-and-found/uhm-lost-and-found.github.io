# UHM Lost and Found

## Table of Contents

* [Overview](#overview)
* [User Guide](#user-guide)
* [Deployment](#deployment)
* [Developer Guide](#developer-guide)
* [Development History](#development-history)
* [Contact Us](#contact-us)

## Overview

UHM Lost and Found is a web application dedicated to posting lost and found items for the University of Hawaii Manoa campus. Departments can post about lost items within their offices, enabling students to recognize their belongings and know exactly where they may find it.

The following tools are used:

* [Meteor](https://www.meteor.com/) for Javascript-based implementation of client and server code.
* [React](https://reactjs.org/) for component-based UI implementation and routing.
* [React Bootstrap](https://react-bootstrap.github.io/) CSS Framework for UI design.
* [MongoDB](https://react-bootstrap.github.io/) database program.
* [meteor-application-template-react](https://ics-software-engineering.github.io/meteor-application-template-react/) template for quickly starting Meteor application development.

It implements a variety of useful design concepts, including:

* Several collections (Clothing, Technology, IDs) for item types.
* Top-level index pages (Add Item, Lost Items, Lost Items Admin) for admin departmental accounts.
* A simple Edit function accessible from the Lost Items page to edit item descriptions or remove items.
* Authentication using the built-in Meteor accounts package along with a Login page.
* Authorization examples: certain pages are public (Landing, Login), while others require departmental admin accounts (Add Item, Lost Items, Lost Items Admin).

## User Guide

This section provides a walkthrough of the UHM Lost and Found user interface and its capabilities.

### Landing Page

The Landing Page is presented to users when they visit the top-level URL of the site.

![](img/M3-landing.png)

### Item Page

From the Landing Page, users may access the Lost Items page to view a catalog of misplaced items on campus.

![](img/M3-Items-page.png)

### Login Page

The Sign-In Page enables the University of Hawaii Manoa departments access to the lost and found items database.

![](img/M3-sign-in.png)

![](img/sign-out-page.png)

### Items Pages (Lost Items, Add Item, Edit Items Admin)

Upon logging in with a department admin account, UHM Lost and Found provides additional pages for adding new items, and another to edit or remove current items from a lost items page.

The Lost Items page will show all the current lost items in the database and their associated locations, the approximate times the items were lost, and the item descriptions. 

![](img/M3-itempage-admin.png)

The Edit Items Admin page allows departments to edit or remove pre-existing lost items.

![](img/M3-editform.png)

The Add Item page allows departments to add a new lost item.

![](img/M3-addItem.png)

### Sign-In

Click on the "Sign In" button in the upper right corner of the navbar. You must have been previously registered in the system to access departmental admin features:

![](img/sign-in-navbar.png)

### Accessing Admin Pages

Once you are signed in with your department or Admin account, two new page links appear (Add Item, and Edit Item) at the top of the navbar. The Admin account will also include Departments and Add Departments links.

![](img/M2-admin-navbar.png)

## Deployment

http://64.23.249.21/


## Developer Guide

This section provides information of interest to Meteor developers wishing to use this code base as a basis for their development tasks.

### Installation

First, [install Meteor](https://www.meteor.com/install).

Second, visit the [UHM Lost and Found application GitHub page](https://github.com/uhm-lost-and-found/uhm-lost-and-found), and click the "Use this template" button to create your repository initialized with a copy of this application. Alternatively, you can download the sources as a zip file or make a fork of the repo.  However you do it, download a copy of the repo to your local computer.

Third, cd into the uhm-lost-and-found/app directory and install libraries with:

```
$ meteor npm install
```

Fourth, run the system with:

```
$ meteor npm run start
```

If all goes well, the application will appear at [http://localhost:3000](http://localhost:3000).

### Application Design

UHM Lost and Found is based upon [meteor-application-template-react](https://ics-software-engineering.github.io/meteor-application-template-react/) and [meteor-example-form-react](https://ics-software-engineering.github.io/meteor-example-form-react/). Please use the videos and documentation at those sites to better acquaint yourself with the basic application design and form processing in UHM Lost and Found.

### Data model

As noted above, the UHM Lost and Found data model consists of item-type collections. To understand this design choice, consider the situation where you want to specify the items associated with a department.


### Initialization

The [config](https://github.com/uhm-lost-and-found/uhm-lost-and-found/tree/main/config) directory is intended to hold settings files.  The repository contains one file: [config/settings.development.json](https://github.com/uhm-lost-and-found/uhm-lost-and-found/blob/main/config/settings.development.json).

This file contains default definitions for Profiles, Projects, and Interests and the relationships between them. Consult the walkthrough video for more details.

The settings.development.json file contains a field called "loadAssetsFile". It is set to false, but if you change it to true, then the data in the file app/private/data.json will also be loaded.  The code to do this illustrates how to initialize a system when the initial data exceeds the size limitations for the settings file.


### Quality Assurance

#### ESLint

UHM Lost and Found includes a [.eslintrc](https://github.com/uhm-lost-and-found/uhm-lost-and-found/blob/main/app/.eslintrc) file to define the coding style adhered to in this application. You can invoke ESLint from the command line as follows:

```
meteor npm run lint
```

Here is sample output indicating that no ESLint errors were detected:

```
$ meteor npm run lint

> uhm-lost-and-found@ lint /Users/MRasavong/github/uhm-lost-and-found/uhm-lost-and-found/app
> eslint --quiet --ext .jsx --ext .js ./imports ./tests

$
```

ESLint should run without generating any errors.

It's significantly easier to do development with ESLint integrated directly into your IDE (such as IntelliJ).

#### End to End Testing

UHM Lost and Found uses [TestCafe](https://devexpress.github.io/testcafe/) to provide automated end-to-end testing.

The UHM Lost and Found end-to-end test code employs the page object model design pattern.  In the [uhm-lost-found tests/ directory](https://github.com/uhm-lost-and-found/uhm-lost-and-found/tree/main/app/tests), the file [tests.testcafe.js](https://github.com/uhm-lost-and-found/uhm-lost-and-found/blob/main/app/tests/tests.testcafe.js) contains the TestCafe test definitions. The remaining files in the directory contain "page object models" for the various pages in the system (i.e. Home, Add Item, Edit Item, etc.) as well as one component (navbar). This organization makes the test code shorter, easier to understand, and easier to debug.

To run the end-to-end tests in development mode, you must first start up a UHM Lost and Found instance by invoking `meteor npm run start` in one console window.

Then, in another console window, start up the end-to-end tests with:

```
meteor npm run testcafe
```

You will see browser windows appear and disappear as the tests run.  If the tests finish successfully, you should see the following in your second console window:

```
$ meteor npm run testcafe

> uhm-lost-and-found@ testcafe /Users/MRasavong/github/uhm-lost-and-found/uhm-lost-and-found/app
> testcafe chrome tests/*.testcafe.js

 Running tests in:
 - Chrome 124.0.0.0 / Windows 11

 uhm-lost-and-found localhost test with default db
 √ Test that HOME page shows up without being logged in
 √ Test that LOST ITEMS page shows up without being logged in
 √ Test that SIGN IN and SIGN OUT work with a departmental account
 √ Test that HOME page appears after signing in with a departmental account
 √ Test that LOST ITEMS page appears after signing in with a departmental account
 √ Test that ADD ITEM page appears after signing in with a departmental account
 √ Test that EDIT ITEM page appears after signing in with a departmental account
 √ Test that SIGN IN and SIGN OUT work with an admin account
 √ Test that HOME page appears after signing in with an admin account
 √ Test that LOST ITEMS page appears after signing in with an admin account
 √ Test that ADD ITEM page appears after signing in with an admin account
 √ Test that EDIT ITEM page appears after signing in with an admin account
 √ Test that DEPARTMENTS page appears after signing in with an admin account
 √ Test that ADD DEPARTMENT page appears after signing in with an admin account


 14 passed (39s)
 $
```

You can also run the testcafe tests in "continuous integration mode".  This mode is appropriate when you want to run the tests using a continuous integration service like Jenkins, Semaphore, CircleCI, etc.  In this case, it is problematic to already have the server running in a separate console, and you cannot have the browser window appear and disappear.

To run the testcafe tests in continuous integration mode, first ensure that UHM Lost and Found is not running in any console.

Then, invoke `meteor npm run testcafe-ci`.  You will not see any windows appear.  When the tests finish, the console should look like this:

```
$ meteor npm run testcafe-ci

> uhm-lost-and-found@ testcafe-ci /Users/MRasavong/github/uhm-lost-and-found/uhm-lost-and-found/app
> testcafe chrome:headless tests/*.testcafe.js -q --app "meteor npm run start"

 Running tests in:
 - Chrome 124.0.0.0 / Windows 11

 uhm-lost-and-found localhost test with default db
 √ Test that HOME page shows up without being logged in
 √ Test that LOST ITEMS page shows up without being logged in
 √ Test that SIGN IN and SIGN OUT work with a departmental account
 √ Test that HOME page appears after signing in with a departmental account
 √ Test that LOST ITEMS page appears after signing in with a departmental account
 √ Test that ADD ITEM page appears after signing in with a departmental account
 √ Test that EDIT ITEM page appears after signing in with a departmental account
 √ Test that SIGN IN and SIGN OUT work with an admin account
 √ Test that HOME page appears after signing in with an admin account
 √ Test that LOST ITEMS page appears after signing in with an admin account
 √ Test that ADD ITEM page appears after signing in with an admin account
 √ Test that EDIT ITEM page appears after signing in with an admin account
 √ Test that DEPARTMENTS page appears after signing in with an admin account
 √ Test that ADD DEPARTMENT page appears after signing in with an admin account


 14 passed (39s)
 $
```

All the tests pass, but the first test is marked as "unstable". At the time of writing, TestCafe fails the first time it tries to run a test in this mode, but subsequent attempts run normally. To prevent the test run from failing due to this problem with TestCafe, we enable [testcafe quarantine mode](https://devexpress.github.io/testcafe/documentation/guides/basic-guides/run-tests.html#quarantine-mode).

The only impact of quarantine mode should be that the first test is marked as "unstable".


## Development History

The development process for UHM Lost and Found conforms to [Issue Driven Project Management](http://courses.ics.hawaii.edu/ics314f19/modules/project-management/) practices. In a nutshell:

* Development consists of a sequence of Milestones.
* Each Milestone is specified as a set of tasks.
* Each task is described using a GitHub Issue and is assigned to a single developer to complete.
* Tasks should typically consist of work that can be completed in 2-4 days.
* The work for each task is accomplished with a git branch named "issue-XX", where XX is replaced by the issue number.
* When a task is complete, its corresponding issue is closed and its corresponding git branch is merged into main.
* The state (todo, in progress, complete) of each task for a milestone is managed using a GitHub Project Board.

The following sections document the current development history of UHM Lost and Found.

### Milestone 1: Mockup Development

The goal of Milestone 1 is to create a set of HTML pages providing a mockup of the pages in the system.

Milestone 1 was managed using [UHM Lost and Found GitHub Project Board M1](https://github.com/orgs/uhm-lost-and-found/projects/2/views/2):

Milestone 2 was managed using [UHM Lost and Found GitHub Project Board M2](https://github.com/orgs/uhm-lost-and-found/projects/4/views/1):

Milestone 3 was managed using [UHM Lost and Found GitHub Project Board M3](https://github.com/orgs/uhm-lost-and-found/projects/5/views/3):

![](images/project-board-1.png)


## Contact Us

UHM Lost and Found is designed, implemented, and maintained by [Victor Pagan](https://vicpagan.github.io/), [Michelle Rasavong](https://mrasavong.github.io/), [Jalen Lum](https://jalenlum.github.io/), and [Sierra Jansons-Dizon](https://sierradizon.github.io/).

[GitHub Organization](https://github.com/uhm-lost-and-found)

[Team Contract](https://docs.google.com/document/d/1WC3Iz7WFFRT5WPFq5RjK-05e0mvruvHO3ZeLoWdCals/edit?usp=sharing)
