---
layout: post
title: Financial Analysis – Excel Basics
date:
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Financial Analysis
tags:
- Analytics
- Financial Analysis
- Business
meta:
author:
  login: carordo
  email:
  display_name:
  first_name: Carlos
  last_name: Ordonez
permalink:
excerpt: Basics of using excel for financial analysis .
---


# Financial Analysis – Excel Basics

## Excel Basics

### Change from Manual to Automatic

Sometimes the data could be in manual to avoid error in the formulas. To
change it to automatic:

-   Go to **Formulas/Calculation Options/** change to **Automatic**

### Use of solver

You can use solver to set a specific value depending on the on the
desired outcome.

-   Find the present value to be 100.00

-   Change the interest rate

-   Set the objective to be the cell of the present value $B$4

-   By changing variable cells to be the interest rate: $B$1

-   Solve

-   Similarly using the constraints by adding the range on which the
    value could change.

-   In this example how to get an A on the last exam

<img src="./assets/images/2022-01-16-Financial_Analysis-Excel_Basics/media/image1.png"
style="width:5.27819in;height:1.97763in" />

> The solver returns 100 for Exam 3

<img src="./assets/images/2022-01-16-Financial_Analysis-Excel_Basics/media/image2.png"
style="width:5.72917in;height:3.21875in" />

### Pivot Tables

Use pivot tables to manage large amounts of data. By clicking inside the
table Excel understands the limits of the data.

In this case, this data for two campanies, the pivot table shows the
average per month

<img src="./assets/images/2022-01-16-Financial_Analysis-Excel_Basics/media/image3.png" style="width:6.5in;height:2.09028in" />

To group it by quarters, highlight the months, right
click/Group/Quarters

<img src="./assets/images/2022-01-16-Financial_Analysis-Excel_Basics/media/image4.png" style="width:6.5in;height:2.80556in" />

### Sensitivity Analysis

Find out how the value of the company changes based on the changes on
some of the inputs.

**Terminal Value** calculates the value in this case from year 4 to
infinitive.

<img src="./assets/images/2022-01-16-Financial_Analysis-Excel_Basics/media/image5.jpeg" style="width:3.2187in;height:1.77304in"
alt="Smoothing capital expenditure in Excel - FM" />

-   Free cash flows are calculated until year 3 then find terminal
    value. Add it to year 3, the calculate Present Value (PV) using NPV

<img src="./assets/images/2022-01-16-Financial_Analysis-Excel_Basics/media/image6.png" style="width:4.70123in;height:2.8785in" />

In order to create a table that shows the variation of the required
return and the grow rate, create a table where the values of each in
these variables are in row column format with the value of the firm at
he corner. **Select the data/ Go to Data/ What-if Analysis / Data Table/
Select row input and grow rate constant/ok**

<img src="./assets/images/2022-01-16-Financial_Analysis-Excel_Basics/media/image7.png"
style="width:3.97696in;height:1.08608in" />

<img src="./assets/images/2022-01-16-Financial_Analysis-Excel_Basics/media/image8.png"
style="width:5.50304in;height:2.15734in" />

We can see the table from changes the values on the left side is equal
to full table on the right side

<img src="./assets/images/2022-01-16-Financial_Analysis-Excel_Basics/media/image9.png" style="width:6.5in;height:1.72569in" />

### How to create a button

Include the Developer tab. Right click on the ribbon select Developer.

<img src="./assets/images/2022-01-16-Financial_Analysis-Excel_Basics/media/image10.png"
style="width:4.42348in;height:4.07896in" />

-   Insert the radio button

<img src="./assets/images/2022-01-16-Financial_Analysis-Excel_Basics/media/image11.png"
style="width:3.66667in;height:1.67708in" />

-   Right click/ Format control/Cell link and select a cell.

-   If another radio button is created, then value of the cell could
    toggle between the buttons. In this example value is changing
    between 1 and 2. If changes, the value changes from 100 to 150

<img src="./assets/images/2022-01-16-Financial_Analysis-Excel_Basics/media/image12.png" style="width:1.625in;height:1.85417in" />

-   Hide the cell by changing the color of number 2 to white

### VLookup – Looks up a value vertically.

In this example we are looking for the name and returning how high the
dog will jump in feet

<img src="./assets/images/2022-01-16-Financial_Analysis-Excel_Basics/media/image13.png"
style="width:4.02439in;height:3.2646in" />
