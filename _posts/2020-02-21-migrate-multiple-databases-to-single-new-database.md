---
layout: post
title: Migrate Multiple Databases to Single New Database
permalink: 2020-02-21-migrate-multiple-databases-to-single-new-database
published: true
---
We are doing a multiple database migration into a new single database. The wrinkle here is that one of the databases we are migrating is a copy of one of the other databases we are migrating. That is, at some point in the past, one division took a copy of the database and started using their own copy.<!--more-->

I'll outline a simplified example of our problem, using just one record type, however we have Account, Contact, Notes, Activities (Calls, Meetings, Tasks), Emails, file attachments etc all thrown in here and related to one another.

What it means now is that there are two input databases to migrate, that have account and contact records that have the same `GUID`'s.

Imagine that the Sales department has following data in the datebase:

## Sales Database (Initial)

| GUID | Name  | Rep  |
|:-----|:------|:-----|
| 123  | Alice | Jane |
| 456  | Bob   | Jill |
| 789  | Cindy | Jane |

And then it was copied and used by the Service department and became this:

## Service Database (Initial)

| GUID | Name  | Rep  |
|:-----|:------|:-----|
| 123  | Alice | Sue  |
| 456  | Bob   | Sue  |
| 012  | Diane | Jill |

Note that the `GUID` for Alice and Bob in both databases is the same.

Naturally enough over time, the records for Alice and Bob diverge from each other so there come to be many differences.

Today both databases are in operation onsite at the client, albeit in different departments.

Migrating these into one database is a problem because if we import the **Sales** database and then import the **Service** the Rep values will be updated and reflect who the Service Rep is and not the Sales Rep.

We don't want to *lose* history of who did what and when, or said what to whom and when.

Thus there must be a better way then just mashing it together and overwriting history.

In our situation right now, we also have a few other considerations:

1. The client is quite ok if there end up being duplicate Account or Contact records, so long as staff can easily see which records belong to which department
1. In the future, we want the client to easily be able to merge records without drama or loss of history
1. We need to run the migration more than once, thus not just an initial `INSERT` of data, but we'll do an *UPSERT*, that is an `UPDATE` if it's already migrated or `INSERT` if it's been added to the old database since the the last run of the migration job
1. We (the team doing the migration) want these migration jobs (tasks) to **Just Work**™

Thusly what we do is map the source database to a new field, and we map the fields that are distincly different, like *Rep*, seperately.

Thus the import source becomes as follows:

## Sales Database (Becomes)

| GUID | Name  | Sales Rep  | Source |
|:-----|:------|:-----------|:-------|
| 123  | Alice | Jane       | Sales  |
| 456  | Bob   | Jill       | Sales  |
| 789  | Cindy | Jane       | Sales  |

## Service Database (Becomes)

| GUID | Name  | Service Rep  | Source  |
|:-----|:------|:-------------|:--------|
| 123  | Alice | Sue          | Service |
| 456  | Bob   | Sue          | Service |
| 012  | Diane | Jill         | Service |

Which when migrated becomes:

## New Database (Migrated)

| GUID | Name  | Sales Rep |Service Rep | Source  |
|:-----|:------|:----------|:-----------|:--------|
| 345  | Alice | Jane      |            | Sales   |
| 678  | Bob   | Jill      |            | Sales   |
| 901  | Cindy | Jane      |            | Sales   |
| 234  | Alice |           | Sue        | Service |
| 567  | Bob   |           | Sue        | Service |
| 890  | Diane |           | Jill       | Service |

Later when they start to merge the records, they'll be able to have the following:

## New Database with Records Merged (Merged)

| GUID | Name  | Sales Rep |Service Rep | Source  |
|:-----|:------|:----------|:-----------|:--------|
| 567  | Alice | Jane      | Sue        | Merged  |
| 890  | Bob   | Jill      | Sue        | Merged  |
| 901  | Cindy | Jane      |            | Sales   |
| 432  | Diane |           | Jill       | Service |

In order to bring these databases together is not complex, but it takes time, planning, good testing and above all, patience.
