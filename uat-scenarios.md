UAT Scenarios --- Habit Tracker MVP
These UAT scenarios are derived from the approved acceptance criteria
and are written in Given/When/Then form.

**_UAT-01 --- First Eligible Habit Increments Streak_**
Given the user has an active streak of 4 and has not completed an
eligible habit today  
When the user completes their first eligible habit of the day  
Then the streak should increase by 1 to 5.
**
**_UAT-02 --- Additional Same-Day Habit Does Not Increment Streak_****
Given the user has a streak of 5 and has already completed one
eligible habit today, causing the streak to become 6  
When the user completes another eligible habit on the same calendar
day  
Then the streak should remain at 6 and should not increment again.

**UAT-03 --- One Missed Day Preserves Streak**
Given the user has an active streak of 5 and the grace period is
available  
When the user completes no eligible habits during the next calendar
day  
Then the streak should remain at 5 and should not increment or
reset.

**UAT-04 --- Two Consecutive Missed Days Reset Streak**
Given the user has an active streak of 5 and has already completed
no eligible habits for one calendar day, using the grace period  
When the user completes no eligible habits for a second consecutive
calendar day  
Then the streak should reset to 0.

**UAT-05 --- Incomplete Scheduled Habit Triggers Reminder**
Given the user has a scheduled habit with a reminder configured and
the habit has not been completed  
When the scheduled reminder time is reached and the habit remains
incomplete  
Then the system should send a reminder notification for that
specific habit.

**UAT-06 --- Completed Habit Suppresses Reminder**
Given the user has completed the specific scheduled habit before its
reminder time  
When the scheduled reminder time is reached  
Then the reminder notification for that habit should be suppressed.

**UAT-07 --- XP Awarded by Difficulty**
Given Morning Walk is configured as Hard, worth 15 XP, and the
user's current XP balance is 40  
When the user completes Morning Walk  
Then the XP balance should increase to 55.

**UAT-08 --- Duplicate XP Is Prevented**
Given the habit is configured for once-daily completion and its XP
has already been awarded for today, with the current XP balance at 50  
When the user attempts to complete the same habit again on the same
calendar day  
Then no additional XP should be awarded and the XP balance should
remain 50.

**UAT-09 --- Milestone Badge Is Awarded**
Given the user has 6 qualifying completion days and has not
previously earned the 7-day milestone badge  
When the user completes an eligible habit for their 7th qualifying
completion day  
Then the system should award the 7-day milestone badge.

**UAT-10 --- Grace Day Does Not Count Toward Milestone**
Given the user has 6 qualifying completion days and has used one
grace day without completing an eligible habit  
When the user completes an eligible habit on the following day  
Then that completion should become the 7th qualifying day and the
7-day milestone badge should be awarded.

Notes / Open Decisions
The 7-day milestone is an MVP example and should be validated with
Analytics/Product evidence before being treated as a final
production threshold.
The allowed frequency/cap for grace-day use remains TBD.
XP values used in UAT examples are illustrative unless formally
approved by Product.
