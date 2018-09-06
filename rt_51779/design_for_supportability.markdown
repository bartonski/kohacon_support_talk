# Body of the talk

## Intro: Why is designing for support important?

### Support is a human activity, and is limited by human capacity

* Hi, My name is Barton Chittenden, I'm from ByWater Solutions. I am, among other things, one of the people that our
partners reach when they call in to our support line. I'd like to talk about Koha from the perspective of someone who
does technical support, and show how that fits in with the design of Koha.

* So, before we go any further, I would like you to think about your last experience with a tech support phone call.

By a show of hands, how many of you are

* picturing pressing phone buttons in an IVR system?
* had a long wait on hold
* got someone on the other end of the line who was reading of a script that included the words "I'm sorry you're having trouble with your _____..."

Were you happy with your experience?
Did the person on the other end of the line listen to you?
Did you *really* believe them when they said they were sorry?

The underlying problem is that when you call into an enormous phone center, you're going to be talking to someone who is taking 150 calls a day, and who has been turned into a robot dealing with the same problems over and over again.

This isn't a good experience for anyone involved. One of the reasons for this is that... 

---

"A computer lets you make more mistakes faster than any other invention with the possible exceptions of handguns and Tequila."

-- Mitch Ratcliffe

* In a previous life, I did support for a VoIP product, a lot like Vonage. We had a feature that we rushed into production. This feature didn't get adequately tested at scale, and it ended up crashing the entire phone network every 20 seconds. It took operations 3 days to figure this out. The whole time, I was left saying "I'm sorry you're having trouble with your VoIP. Yes, we are aware of this issue; I don't have a resolution at this time". Those were the three longest days of my life in tech support. It sucked my compassion dry.

* Koha isn't structured like this -- it's not deployed in a monolithic environment; it tends to be installed on a network of much smaller servers. However, one or more bad bugs in a major release *can* create a slow motion version
of this, where support staff is not overwhelmed in a single day, but worn down over a period of time. The effects on
our compassion, our ability to listen and communicate effectively are diminished, and that's bad for everyone.

* This talk is aimed at looking at some of the design decisions that would make Koha a little easier to support, either for a systems librarian at a site which has their own Koha instance, or for a support vendor.

---

### Elements of support

- Communication with the partner
    * At ByWater, we use the term 'reference interview'
    * Expectation vs. reality
- Classifying the issue
    * Assigning urgency and importance
    * Allows us to find similar problems, perhaps the problem has already been solved.
    * Finding the right person to solve the problem
- Replicating the issue
    * If we can see the problem and make it happen, we know that we have effective communication
    * This also makes troubleshooting easier
- Trouble-shooting
    * Getting data from the system efficiently
    * Finding the root-cause of an issue
    * Is this a bug or a feature?

### Challenges

### Communication with the partner

* Unclear interfaces
    * Circulation rules
* Interfaces that are difficult to describe (example: acquisitions )
* Inconsistent interfaces (example: notices and slips)

### Classifying the issue

* Organization of the system
* Error messages hidden by plack
* Error messages not consistently recorded in bugzilla
* Organization of Bugzilla does not always match organization of Koha.

### Replicating the issue

* Configuration can be spread across the system; non-obvious causation.
* Hard to extract a minimal amount of data to re-create problems.
* Interfaces that are difficult to describe

### Trouble-shooting

* Not always obvious what the system was designed to do.
    * Is this a bug or a feature?
* Gathering data can be challenging
    * We don't always have historical data
    * Data can be linked in non-obvious ways
* Parts of the problem space poorly defined
* Getting data from the system efficiently
* Finding the root-cause of an issue

### Solutions

#### Communication with the partner

* Unclear interfaces
    * Circulation rules
* Interfaces that are difficult to describe (example: acquisitions )
* Inconsistent interfaces (example: notices and slips)

#### Classifying the issue

* Organization of the system
* Error messages hidden by plack
* Error messages not consistently recorded in bugzilla
* Organization of Bugzilla does not always match organization of Koha.

#### Replicating the issue

* Configuration can be spread across the system; non-obvious causation.
* Hard to extract a minimal amount of data to re-create problems.
* Interfaces that are difficult to describe

#### Trouble-shooting

* Not always obvious what the system was designed to do.
    * Is this a bug or a feature?
* Gathering data can be challenging
    * We don't always have historical data
    * Data can be linked in non-obvious ways
* Parts of the problem space poorly defined
* Getting data from the system efficiently
* Finding the root-cause of an issue

----

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

## What does designing for support-ability give us?

* The ability to identify patterns in support issues
* The ability to easily capture system configuration
* The ability to extract a sample of data to replicate issues and see common mis-configurations
* Discover-ability
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
* Accountlines date-format
* Report scheduler

## Other thoughts

* Capacity and scaling issues are always hard

Life cycle of a support issue

- Something happens that the user perceives as wrong.
- User calls support, describes issue
- Support person works to
    * rephrase the issue in language that everyone can agree on
    * narrow the description, find out what is or is not relevant
    * replicate the issue
        * This helps reenforce communication -- if we're seeing the same responses from the system, we're largely in sync.
    * Classification -- what kind of issue is this?
        * what part of the system are we looking at?
            * circulation?
            * cataloging
            * OPAC related?
        * is this something that we've seen before?
        * who can/should fix the problem?
    * find a work around
    * report bugs
