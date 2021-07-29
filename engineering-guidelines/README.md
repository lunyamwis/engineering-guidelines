# engineering-playbook

# Introduction

This wiki contains the description of the conventions, tools and workflow to be used in projects.


## Table of Content

- [Branch Naming](#branch-naming)

- [Commit Message](#commit-message)
  - [Message Header](#message-header)
  - [Message Body](#message-body)
  - [Message Footer](#message-footer)
  - [Message Example](#message-example)

- [Merge Request](#merge-request)
  - Merge Request Title
  - Merge Request Description Template
  - Merge Request Example
  - Merge Request Etiquette

- [Open Projects Story](#open-projects-story)
  - Feature Story
  - Bug Story
  - Chore Story

- [Repo Readme](#repo-readme)

- [ESLint](#eslint)

- [Mocha, Chai and Chai-http assertion library](#mocha-chai-and-chai-http)

- [JSDocs](#jsdocs)


## Branch Naming

Branches created should be named using the following format:

`{story type}-{story summary}-{open projects id}`

`story type` - Indicates the context of the branch and should be one of:

    ft == Feature
    bg == Bug
    ch == Chore

`story summary` - Short 2-3 words summary about what the branch contains

`open projects id` - The Id of the open projects story associated with the commit

Example

`ft-resources-rest-endpoints-111504508`

## Commit Message

A commit message consists of a **header**, a **body ** and a **footer**, separated by a blank line.

Any line of the commit message cannot be longer than 100 characters! This allows the message to be easier to read on gitlab as well as in various git tools.

```
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

These rules are adopted from the [AngularJS commit convention.](https://docs.google.com/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/edit)

#### Message Header

The message header is a single line that contains succinct description of the change containing a type, an optional scope and a subject.

`##### <type>` This describes the kind of change that this commit is providing.

    feat (feature)
    fix (bug fix)
    docs (documentation)
    style (formatting, missing semi colons, …)
    refactor
    test (when adding missing tests)
    chore (maintain)

`#####<scope>` Scope can be anything specifying place of the commit change. For example events, kafka, user_model, authorization, authentication, loginPage, etc...

`#####<subject>` This is a very short description of the change.

    use imperative, present tense: “change” not “changed” nor “changes”
    don’t capitalize first letter
    no dot (.) at the end

#### Message Body

    just as in subject use imperative, present tense: “change” not “changed” nor “changes”
    includes motivation for the change and contrasts with previous behavior

[http://365git.tumblr.com/post/3308646748/writing-git-commit-messages](http://365git.tumblr.com/post/3308646748/writing-git-commit-messages)

[http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
Message Footer](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)

#### Message Footer

Finished, fixed or delivered stories should be listed on a separate line in the footer prefixed with “Finishes”, “Fixes” , or “Delivers” keyword like this:

[(Finishes|Fixes|Delivers) #OP_STORY_ID]

#### Message Example

feat(kafka): implement exactly once delivery

- ensure every event published to kafka is delivered exactly once
- implement error handling for failed delivery

[Delivers #130635935]

## Merge Request
#### Merge Request Title

The Merge Request title should be named using the following format:

`#[STORY_ID] [Story description]`

#### Merge Request Description Template

The description of the Merge Request should contain the following headings and corresponding content in Markdown format.

```
#### What does this Merge Request do?
#### Description of Task to be completed?
#### How should this be manually tested?
#### Any background context you want to provide?
#### What are the relevant open projects stories?
#### Screenshots (if appropriate)
#### Questions:
```

#### Merge Request Example

#### Merge Request Etiquette

It is our belief that Merge Request reviews should not negatively impact a team’s ability to deliver features. Merge Requests that take too much time to get reviewed can hinder on a team’s progress. As such, we practice the following behaviours when raising Merge Requests:

    When I raise a Merge Request, I specifically assign a developer or engineering team as reviewer
    When I raise a Merge Request, I notify the reviewer(s) on rocketchat in a public channel
    The reviewer(s) can re-assign the Merge Request to someone else (e.g. to a Senior Engineer)
    The reviewer(s) has a 3 hours SLA to review the Merge Request
    If SLA is not met, I can merge the unreviewed Merge Request if and only if:
        All the Merge Request checks are passing (CircleCI, CodeClimate, Test Coverage)
        I communicate in #technology rocketchat channel that I am merging an unreviewed Merge Request
        I immediately take ownership of fixing any issues that arise from merging the Merge Request

## Open Projects Story
#### Feature

A Feature story should contain the following information

**Title** : one line describing the story

**Description** : a detailed description of the story. The description should include acceptance criteria

Example

```
Title:
As a Director of Success (DoS), I should be able to initiate a "Share with Fellows" action for engagements with "Completed" needs assessments to Fellows who are not externally placed.

Description: 
* As a DoS, I should be able to select and share engagements with "Completed" Needs Assessment status
* After sharing an engagement, it shows up in the open engagement view
```

Note: Every story title should include the word ‘should’ as opposed to ‘can’. e.g. It’s unclear whether the story “User can delete comment” is a feature or a bug. “User should be able to delete comment” or “User should not be able to delete comment” are much clearer: the former is a feature, the latter a bug.

#### Bug

A bug story should contain the following information:

**Title** : A short description of the bug.

**Description** : What is currently happening? What should be happening?

**Steps To Reproduce** : Outline the steps to reproduce/show the bug.

**Resources** : Include screenshots and other assets to help explain/show the bug.

Example

```
Title:
Unwanted spaces should not appear between widgets.

Description:
The number of widgets showing per row is inconsistent.
When users view their dashboard, each row should contain 2 widgets per row.

Steps To Reproduce:
- Login to Skilltree dashboard.
- Some rows display unwanted spaces in between the widgets.

Resources:
Attach a screenshot of the error caused by the bug if applicable.
```


#### Chore

A chore story should include the following information:

**Title** : A short description of what needs to be done.

**Description** : Why is it needed? Does it help the team go faster or is it a dependency that could cause problems in the codebase if it’s not done?

**Acceptance Criteria** : These should include conditions that must be met for the chore to be accepted.

Example

```
Title:
Setup CI for user management service

Description:
Stable CI setup will make it easy to integrate our code while ensuring that all defined tests are passing per integration.

Acceptance Criteria:
Working CI integration with circle CI.
```

## Repo README

There’s a lot we can do to encourage code reuse, sharing and onboarding of new team members. For instance, Every gitlab repo should fill in the short description and website link at the top. Also, a gitlab repository needs a proper README to best help out our teammates.

The belief here is that a repo should have a few defining traits to make it easy for anyone to understand it’s purpose, set it up, run it’s tests, and work towards contributing to it.

Each Repo’s README should follow this basic structure:

```
## Repo Name [codeclimate badge] [testing badge]

1 sentence tag line

# Description

3-5 sentences describing the code and what it's purpose is

## Documentation

List of endpoints exposed by the service

## Setup

Step by step instructions on how to get the code setup locally. This may include:

### Dependencies

List of libraries, tools, etc needed (e.g. yarn, node.js, python, etc)

### Getting Started

List of steps to get started (e.g. clone repo, submodule, .env file, etc)

### Run The Service

List of steps to run the service (e.g. docker commands)

### Microservices

List out the microservices if any that this repo uses

## Testing

Step by step instructions on how to run the tests so that the developer can be sure they've set up the code correctly

## Contribute

Any instructions needed to help others contribute to this repository

## Deployment

Step by step instructions so that the developer can understand how code gets updated
```

## ESLint

Eslint is a linting library (tool). It is essentially designed to raise flags whenever a coding convention is not implemented correctly. In this case the style guide is Airbnb. See [ESLint ](https://eslint.org/)for more details.

AirBnB Guide is a set of predefined rules for ESLint style configuration.

## Mocha, Chai and Chai-http

Mocha is a feature-rich JavaScript test framework running on Node.js and in the browser, making asynchronous testing simple and fun and works with other tests libraries like Chai and Chai-HTTP.

See [Mocha ](https://mochajs.org/) and [Chai ](https://www.chaijs.com/)for more information.

## JSDocs

JSDocs is a tool for commenting and documentation for javascript-based APIs. Programmers can add documentation describing the application programming interface on the code that was created. See [JSDoc ](https://jsdoc.app/) for more information.
