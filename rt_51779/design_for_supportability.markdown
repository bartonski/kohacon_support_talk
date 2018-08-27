# Body of the talk

## Intro: Why is designing for support important?

### Support is a human avtivity, and is limted by human capacity

* Slide title

"A computer lets you make more mistakes faster than any other invention with the possible exceptions of handguns and Tequila."
-- Mitch Ratcliffe

* In a previous life, I did support for a VoIP product, a lot like Vonage. Our sales group found out that there was a feature that they had hyped that wasn't working the way they said it had, and so they put pressure on operations to rush the feature into production. This fix didn't get adequately tested at scale, when we put it into production, it ended up taking the entire phone network offline every 20 seconds. It took operations 3 days to figure this out. Those were the three longest days of my life in tech support. It sucked my compassion dry.

---


Life cycle of a support issue

- Something happens that the user perceives as wrong.
- User calls support, describes issue
- Support person works to
    * narrow the description, find out what is or is not relevant
    * rephrase the issue in language that everyone can agree on
    * replicate the issue
    * Triage:
        * is this a education / configuration issue? Send to Education department.
        * is this a data issue? => Send to data department.
        * is this a bug? => File bug.
    * find a work around
    * report bugs


## Three legs to the support table

- Communication
- Getting to the root of the problem efficiently
- Replicating the issue

### Communication

#### User Interface Issues

* Unclear interfaces
* Interfaces that are difficult to describe (example: acquisitions )
* Inconsistent interfaces (example: notices and slips)

### Getting to the root of the problem efficiently

* Support interface

#### Data issues

* Global variables
* Bad database design has support consequences
* Magic variables
* Food processed data
* Grey areas, scary basements, loose specs

### Replicating the issue

* All information needed to trouble-shoot an issue should be available in one place

## Logging

### Trade offs

* Detail
* Performance
* Disk space

## What does designing for supportability give us?

* The ability to identify patterns in support issues
* The ability to easily capture system configuration
* The ability to extract a sample of data to replicate issues and see common mis-configurations
* Discoverability
* Clear categories of issues
* Easy to describe
* Thin user interfaces - logic lies below the interface for testability purposes

## Support Hell

* Complex problems
* Hidden causes
* Intermittent issues
* Hard for end users to describe
* Affects lots of users
* Doesn't occur in test systems
* Only occurs in certain configurations
* Configuration is hard to replicate
* Smoke tests miss failures
* Failures corrupt data and are silent
* Grey, unspecified logic
* Niggling issues that we should have filed a bug about a long time ago
* Recursive structure that isn't (?)
* Global variables
* Magic bits
* Non-uniform environments
* Hard to replicate problems because configuration is too in depth

## Case study

* Once upon a time issue
* DIGEST notices
* Accountlines dateformat
* Report scheduler

## Other thoughts

* Capacity and scaling issues are always hard
