---
layout: post
title: "Crontab Basic Example"
description: "An overview of using Crontab"
tags: [Crontab]
---

After having recently moved to a Mac from a Windows laptop, the loss of many features that I took for granted has been daunting.
Losing the Task Scheduler is one such example. However, we have Crontab to the rescue.

## Crontab

A cron job is just a command to run and the schedule that it should be run on.

Crontab is just a collection of those cron jobs. So it does appear we are losing a lot of functionality if you compare it to Task Scheduler, such as having triggers that are not based around time only. I thought the loss of such features and the GUI would be a hinderance to crontab, but so far it really hasn't been. I don't think I've ever made a scheduled task that wasn't based on a timed schedule and the GUI is usually massively unresponsive, especially when remoting on to a server.

## -l

To look at what cron jobs are currently set up you use the command;

    crontab -l

This will list out all of the commands and their respective schedules.

## -e

In order to edit the crontab use;

    crontab -e
    
This will open the crontab file for editing; for me this opens in Vim by default.

To make a chang in Vim, press "I" to put it in "Insert" mode, make your changes then exit by first pressing escape to leave "Insert" mode followed by ":wq" to write and quit.

## cron schedule

A cron schedule is made up from 5 time parts to set the schedule. Minute, hour, day of month, month, and day of week.

| *      | *    | *            | *     | *           |
|--------|------|--------------|-------|-------------|
| minute | hour | day of month | month | day of week |

For example, to run a command at 2:30pm every day the schedule would be;

    30 14 * * *
    
To have a command run every 10 minutes;

    */10 * * * *
    
To run a command at quarter past and quarter to every hour;

    15,45 * * * *
    
[crontab.guru](https://crontab.guru) is a great site where you can test out your schedule.
