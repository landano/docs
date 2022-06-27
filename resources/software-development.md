---
description: The methodology used by the Landano project to develop its software
---

# Software development

## Purpose

Establishing a well-defined software development methodology is a recognized best practice for delivering IT solutions on time, within budget, with minimal bugs. When all team members implement it consistently then such a methodology creates products that are easier to maintain and enhance while delivering software that solves real world problems for end-users.

The purpose of this document is to describe Landano’s software development methodology as a point of reference for software developers, product owners, and end users as well as other stakeholders such as project sponsors or other software developers that want to integrate our code and/or practices.

## Scrum methodology

The Landano software development methodology is a customized version of SCRUM which is the predominant software development methodology within the Agile Software development family of practices.

It follows this process:

1. User stories are developed in order to maximize end-user business value.
2. Related or inter-dependent user stories are bundled into “epics” for higher-level organization and planning purposes.
3. Each story is added to the Backlog lists which imposes a priority order. These priority rankings will be established by the Project Owner.
4. Once the Backlog is created, the SCRUM team will work through the tasks on the list from top to bottom, dividing the work into “sprints”. A sprint is just a short, time-boxed period (e.g. 1 week, 2 weeks) when a scrum team works to complete a set amount of work. A Sprint will be initiated by a Refinement Meeting wherein the team will decide which backlog items can be accomplished within a short period of time (i.e. 2 weeks).
5. The team will play Planning Poker in which a SCRUM team predicts the necessary time to complete each of the tasks within a sprint and assign labels accordingly to each task to indicate the scale of work required.
6. The sprint will include regularly scheduled standup meetings. In most projects, these are held daily but these could be held less regularly (e.g. weekly) or asynchronous in a chat room for projects where team members are widely dispersed across time-zones.
7. In the standup meeting, each team member will report:
   1. What I worked on since our last sprint meeting.&#x20;
   2. What I am working on next.&#x20;
   3. What blockers I have that are stopping me from moving ahead on what I am working on.
8. The Sprint should conclude with three deliverables:
   1. An end-user software demo that can be shared with project Stakeholders for the purpose of receiving user feedback.
   2. Well-documented source code that includes automated tests that address the user stories.
   3. A retrospective meeting wherein team members can reflect on how the Sprint went and what may be improved upon in the next.

### User stories

User stories are descriptions of real world scenarios that can be enhanced with a software-based solution. Their purpose is to capture a description of a software feature from an end-user perspective and establish a common understanding about the software functionality between developers and all other stakeholders.

The standardized format for user stories will be:

`As a [type of user], I want to [achieve something with the software] so that I can [do my work].`

Some examples include:

`As a Village Chief, I want to access the Cadastral boundaries of our communal land so that I can accurately manage my fiduciary responsibilities.`

****
