---
layout: post
title: "Acceptance Criteria in Scrum"
quote: "As agile development teams, definitely you may familiar with acceptance criteria. But there are many occasions teams feel a bit complicated when separating out acceptance criteria and test combinations."
image:
      url: /media/medium/denise-jans-1203943-unsplash.jpg
video: false
comments: true
author_name: Eranga Rajapaksha
author_url: https://github.com/EmblaTech
author_pic: istockphoto-836272842-612x612.jpg
---

<style type="text/css"> #post-info { background-color: rgba(0,0,0,.5); padding: 10px; } </style>



As agile development teams, definitely you may familiar with acceptance criteria. But there are many occasions teams feel a bit complicated when separating out acceptance criteria and test combinations. By definition, acceptance criteria are “Conditions that a software product must satisfy to be accepted by a user, customer or other stakeholder.”(Microsoft Press) That means a set of statements which describes user’s requirement or features and functionalities of an application.

## **User stories and acceptance criteria**

In agile we write user stories to describe a feature that should be implemented by the team. Normally the syntax is,
> **As system admin** I want to** add a user** to the system so that they **can access the system**

But just writing a user story in standard way won’t explain the whole requirement to the development team. Therefore the user story is incomplete without acceptance criteria.

## **Write acceptance criteria**

There are four important rules which helps you to write acceptance criteria

1. See the feature as an end user

1. Consider functional, nonfunctional and performance criteria

1. Clear and simple

1. Not test combinations

## ***See the feature as an end user***

Acceptance criteria are simple statements of requirements. From the first point you have to see the requirements from the user’s perspective. Think how you are going to demonstrate the feature and how the specific user will feel when using the application. Then it helps to build a product which will “work as expected by end user”. User’s age, education level, context always matters when enhancing user experience. Therefore list down all the acceptance criteria based on who’s going to use it.

Ex:
> “Doctor wants to select drug names which can be printed in the prescription”

This gives a better idea about how the team should implement the application is usable to doctors. Understand that when the role changed whole implementation will change.

## ***Consider functional, nonfunctional and performance criteria***

Acceptance criteria should be written based on functional, nonfunctional and performance criteria. It is important to write negative and positive scenario as well. Then it will help you to define the scope of the user story.

Ex:

### For the login feature
> **Functional**: Successfully logged in users should be navigated to home page with a welcome message
> **Nonfunctional**: Welcome message should display in the upper right corner of the home page
> **Performance**: Home page should load within 1 seconds

## ***Clear and simple***

Acceptance criteria should be written in simple language. It should explain “what to implement” not “How to implement”.

Ex:
> Team lead can approve all the pending leaves of his/her team

### But not
> Team lead can click on approving button which displays against the pending leaves of his/her team

## ***Not test combinations***

The important thing is not to mess — up with test combinations. See the below example user story and acceptance criteria
> **User story**: As a user, I want to see “Average working hours” so that, I can know my average working hours for the week

### Acceptance criteria:

1. Display average working hours for the current week

1. Display up to 2 decimal points

1. If user haven’t worked for the week display 0.00

From the above 3 acceptance criteria do we need to write 3rd one. Definitely not. Because it is a test combination of 1st acceptance criteria. Be mindful when writing acceptance criteria not to include test combinations.

Acceptance criteria are the most important part of a user story which guide the team to build right application. Therefore, always make sure to add acceptance criteria and define the scope of the user story before start the sprint.
