Aware – MVP Requirements Document
============================

Overview
--------

Aware is an application designed to help users gain awareness of how they spend their time. It is composed of a neutral, bias-free backend and a variety of potentially opinionated frontends tailored to specific use cases (e.g., weight loss, time tracking for freelancers).  Ultimately, aware is intended to help users reflect on how they actually spent their day, promote awareness, and provide a minimal intervention structure.  A neutral data store and API responsible for recording and storing actual day-to-day activities without judgment or prescriptive goals.

* [Key Requirements](#Key-Requirements)
* [Backend (Core System)](#Backend)
* [Front End](#FrontEnd)


Key Requirements
----------------

### Backend
#### Event Tracking
1. Record the start of an event or activity
2. Automatically calculate duration from the current task’s start to the next task’s start
3. Store raw start and end timestamps


#### Event
Support predefined event types:
1. Type
2. Start Epoch
3. Measurement
4. Label

#### Activity
Support predefined activity types:
1. Nourishment (prep, eating)
2. Exercise
* Run
* Lift Weights
* Swim
* Walk
3. Work
* Self-Improvement
* Projects (e.g., coding, database work)
    * User defined
* Professional Development
* Billable Hours
4. Bodily Functions
5. Hygiene
* Bathe
* Brush Teeth
* Cut Hair
6. Mental Relaxation
7. Non-tracked Time
8. Housework
* Laundry
* Clean Bathroom
* Make Bed
* Clean Bedroom

Notes are happening too. They go to Events and Activities optionally.

Allow 1:M relationship between activity instances and types (multi-type tagging)

#### Data Integrity & Neutrality

* Backend makes no assumptions or judgments about activities
* Store metadata needed for rich reporting but defer interpretation to the frontend

### Frontend

#### Input

* MVP frontend allows user to record end of activity
* Select type for recorded activity.

#### Reporting

* Produce structured text output in the form of:
    ```strftime('%R%t%d %B %Y%t') + "activity_type=.*;" + tab + "duration=strftime('%T');"```

Future Frontend Concepts
------------------------

* Freelancer Time Tracker
    * Emphasizes billable hours and contract tagging
* Health Tracker
    * Focused on nourishment, exercise, and hygiene with goals and analytics
* Professional Growth Tracker
    * Highlights self-improvement and skill development over time
