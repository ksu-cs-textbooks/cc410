---
title: "Assignment Requirements"
weight: 10
pre: "1. "
---

This page lists the example project requirements for **Example 7A** in CC 410. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

This example will cover some concepts related to parallel programming. This is meant to be an exploratory project only, so requirements are very loose. 

## General Requirements

* **No style or documentation requirements will be enforced for this example.**

## Assignment Requirements

* `ParallelOne`
  * Update `ParallelOne` following the video to use **4 Threads**.
  * Run the program a few times and observe a race condition. **Take a screenshot of the race condition** and store it in a file named `race` in the project folder.
  * Update `ParallelOne` to properly use locks to prevent a race condition.
  * Run the program a few times and verify that no race condition occurs. **Take a screenshot of the program running correctly** and store it in a file named `lock` in the project folder. 
  * See [Take a Screenshot](https://www.wikihow.com/Take-a-Screen-Shot-(Screen-Capture)) on Wikihow for details on how to take a screenshot. On Windows, you can use the "Snipping Tool" to grab only a portion of the screen.
  * See [Uploading Files](https://docs.codio.com/project/ide/navigation/#uploading-files) in the Codio documentation for how to upload a screenshot.
* `ParallelTwo`
  * Update `ParallelTwo` following the video to handle blocking and an arbitrary number of threads.
  * Run the program with varying numbers of threads (1 - 10 recommended) and graph the number of threads vs. the time taken. 
  * Submit your graph as an image file named `graph` in the project folder. 
  * See [How to Make a Single Line Graph in Excel](https://www.smartsheet.com/line-graphs-line-charts-excel#:~:text=Highlight%20both%20columns%20of%20data,tab%20%3E%20Line%20Chart%20%3E%20Line.) for instructions.
* Based on the results of the `ParallelTwo` exercise, write a short blurb in a `README.md` file in the project folder:
  * How did the number of threads impact amount of time taken to complete the work?
  * What does that result tell us about the hardware available on the Codio system?

See below for some example screenshots and graphs. The sample graph shows results for both Java and Python, but your graph will only include one language.
  
## Time Requirements

Completing this project is estimated to require 1 hour.

## Grading Rubric

This assignment will be graded based on the rubric below:

* Updates to `ParallelOne` - 30%
* `race` screenshot - 10%
* `lock` screenshot - 10%
* Updates to `ParallelTwo` - 20%
* `graph` image - 20%
* `README.md` file - 10%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.

---
---
---

## Sample Screenshots

###### Race

![Race Screenshot](/images/e7a/race.png)

##### Lock

![Lock Screenshot](/images/e7a/lock.png)

##### Graph

![Graph](/images/e7a/graph.png)
