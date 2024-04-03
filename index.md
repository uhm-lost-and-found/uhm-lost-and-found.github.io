# UHM Lost and Found

## Table of Contents

* [Overview](#overview)
* [User Guide](#user-guide)
* [Development Notes](#development-notes)
* [Development History](#development-history)
* [Example Enhancements](#example-enhancements)
* [Team](#team)

## Overview

UHM Lost and Found is a web application dedicated to posting lost and found items for the University of Hawaii Manoa campus. Departments can post about lost items within their offices, enabling students to recognize their belongings and get in touch with the respective departments to arrange pick-up.

The following tools are used:

* [Meteor](https://www.meteor.com/) for Javascript-based implementation of client and server code.
* [React](https://reactjs.org/) for component-based UI implementation and routing.
* [React Bootstrap](https://react-bootstrap.github.io/) CSS Framework for UI design.
* [MongoDB](https://react-bootstrap.github.io/) database program.
* [meteor-application-template-react](https://ics-software-engineering.github.io/meteor-application-template-react/) template for quickly starting Meteor application development.

It implements a variety of useful design concepts, including:

* Several collections (Clothing, Technology, IDs) for item types.
* Top-level index pages (Add Item, List Items, Third Page) for admin departmental accounts.
* A simple Edit function accessible from the List Items page to edit item descriptions or remove items.
* Authentication using the built-in Meteor accounts package along with a Login page.
* Authorization examples: certain pages are public (Landing, Login), while other pages require departmental admin accounts (Add Item, List Items, Third Page).

## User Guide

This section provides a walkthrough of the UHM Lost and Found user interface and its capabilities.

### Landing Page

The landing page is presented to users when they visit the top-level URL of the site.

![](images/landing-page.png)

### Login Page

The login page enables the University of Hawaii Manoa departments access to the lost and found items database.

![](images/login-page.png)

### Items Pages (Add Item, List Items, Third Page)

Upon logging in with a department admin account, UHM Lost and Found provides three pages to add new items, edit or remove current items, and (insert third page description).

The Add Item page allows departments to add a new lost item.

![](images/add-item-page.png)

The List Items page shows all the current lost items in the database and their associated locations, the approximate times the items were lost, and the item descriptions. 

![](images/list-items-page.png)

Finally, the (third page) allows departments to...

![](images/third-page.png)


### Login

Click on the "Login" button in the upper right corner of the navbar. You must have been previously registered in the system to access departmental admin features:

![](images/login2-page.png)

### Accessing Admin Pages

Once you are logged in with your departmental admin account, you will see three new pages at the top of the navbar:

![](images/new-navbar.png)


## Development Notes

UHM Lost and Found is meant to illustrate an example of a website University of Hawaii Manoa departments can use to list lost and found items in their offices. For a real-life application, several additional security-related changes must be implemented:

* Use of email-based password specification for users, and/or use of an alternative authentication mechanism.
* Use of https so that passwords are sent in encrypted format.


### Continuous Integration

![ci-badge](https://github.com/bowfolios/bowfolios/workflows/ci-bowfolios/badge.svg)

UHM Lost and Found uses [GitHub Actions](https://docs.github.com/en/free-pro-team@latest/actions) to automatically run ESLint and TestCafe each time a commit is made to the default branch.  You can see the results of all recent "workflows" at [https://github.com/bowfolios/bowfolios/actions](https://github.com/bowfolios/bowfolios/actions).

The workflow definition file is quite simple and is located at
[.github/workflows/ci.yml](https://github.com/bowfolios/bowfolios/blob/main/.github/workflows/ci.yml).

## Development History

The development process for UHM Lost and Found conforms to [Issue Driven Project Management](http://courses.ics.hawaii.edu/ics314f19/modules/project-management/) practices. In a nutshell:

* Development consists of a sequence of Milestones.
* Each Milestone is specified as a set of tasks.
* Each task is described using a GitHub Issue, and is assigned to a single developer to complete.
* Tasks should typically consist of work that can be completed in 2-4 days.
* The work for each task is accomplished with a git branch named "issue-XX", where XX is replaced by the issue number.
* When a task is complete, its corresponding issue is closed and its corresponding git branch is merged into master.
* The state (todo, in progress, complete) of each task for a milestone is managed using a GitHub Project Board.

The following sections document the current development history of UHM Lost and Found.

### Milestone 1: Mockup Development

The goal of Milestone 1 is to create a set of HTML pages providing a mockup of the pages in the system.

Milestone 1 was managed using [BowFolio GitHub Project Board M1](https://github.com/bowfolios/bowfolios/projects/1):

![](images/project-board-1.png)

## Example Enhancements

There are a number of simple enhancements that can be added in development later:

* Display an email icon that links to a mailto: for each associated user.
* Display the home page for each project as a home icon. Click on it to visit the home page.
* Add social media accounts to the profile (Instagram, Twitter, Facebook) and show the associated department accounts.
* It would be nice for users to only be able to edit the items that they have created.  Add an "owner" field to the item collection, and then only allow a user to edit an item definition if they own it.
* The testcafe acceptance tests might only test successful form submissions. Add a test in which you fill out a form incorrectly (perhaps omitting a required field) and then test to ensure that the form does not submit successfully.

## Team

UHM Lost and Found is designed, implemented, and maintained by [Victor Pagan](https://vicpagan.github.io/), [Michelle Rasavong](https://mrasavong.github.io/), [Jalen Lum](https://jalenlum.github.io/), and [Sierra Jansons-Dizon](https://sierradizon.github.io/).
