# Pennant
Pennant is a program that supplements certain *inconvenient* parts of Banner.

- Reading through the schedule of classes
- Searching for classes
- Reading up classes

Banner is okay at these things, but it's clunky and requires a lot of clicks to get through. Also, you have to deal with an internet application.

Pennant serves three functions

- Scrape the Schedule of Classes from Banner
- Package a neatly formatted data set of classes
- Provide an offline frontend for browsing through classes.

Pennant cannot replace Banner, but it should provide a more convenient way to work with Banner.

## Development
This project shall be informally managed as IEEE@UCR's fifth project. Implementation and maintenance shall be done by a volunteer committee, led or advised by the Webmaster. Later, we could implement distinct lead positions similar to other projects.

The committee shall meet weekly. Developers shall follow professional-like practice and conduct regular code reviews.

This project is different from IEEE@UCR's other projects as it focuses exclusively on software development. This should have greater appeal to the programming-oriented members who join IEEE@UCR. Furthermore, this project is independently run and not meant for any kind of hackathon or national competition. This project is expected to change over time - should it reach a state where development or maintenance is no longer needed, the Webmaster ought to plan another software project.

The purpose of this project is to provide professional-level experience while creating tools with long-lasting, real-world utility.

## Inspiration
- [Firehose](https://firehose.guide/): a scheduling program for MIT students.
- [classflow](https://github.com/OrderFromChaos/classflow)
  - [Course Sorter](https://github.com/tobiask190/Course_Sorter)
  - [Course Planner](https://github.com/Varhagna/Course-Planner)

## Code
Pennant is written in C# and runs on .NET 5.0. For the scraper, we use the HTML Agility Pack and Chrome web driver.

## Terminology
- A *course* is a class.
- A *section* is an implementation of a course with a given time, instructor, location, etc. There are several kinds of sections
  - Lecture
  - Discussion
  - Laboratory

## Scraper
The web scraper opens a Chrome browser onto Banner and clicks through it (this is just as hacky as it sounds), saving pages of class listings into HTML files. Most section info is already stored in the HTML data.

To navigate the page, we use a combination of clicks and tab presses. To do this, we need to be aware of the pixel positions of various buttons - we can assume that the button positions are not subject to change in the future.

We also want to get Linked Sections info and general details about each course. This information is not stored in the class listing; we will have to click through View Linked Sections to get Linked Sections info and click on each class name to get its general description info.

## Parser
The parser reads the HTML files returned by the scraper and constructs Objects representing each class and all its info. We can serialize these Objects to provide a pre-packaged data set of classes for offline use.

### Data format
To be specified

## Scheduler
The scheduler is an offline user interface that lets you search and pick classes to build a term plan. Exact design decisions are to be determined.

## Scope & Progress
- [ ] Scrape the Schedule of Classes for a given term from Banner
  - [X] Scrape section info
  - [ ] Scrape Linked Sections
  - [ ] Scrape course info
- [ ] Parse class data into objects
  - [X] Parse section info
  - [ ] Parse Linked Sections
  - [ ] Parse course info
  - [ ] Generate a well-packaged data set
- [ ] Create a frontend to select classes for a term
  - [ ] Search classes by various criteria
  - [ ] Provide basic suggestions for classes based on user-specified pre-requisites
### Not in scope
- Automatically arrange a long-term schedule for you - this is probably an NP-hard problem that we can't solve.
