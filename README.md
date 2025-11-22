# Fitness Tracker Dashboard (Power BI)🔥

A modern, user-focused Power BI dashboard built to help gym owners and trainers visualize revenue, memberships, workout performance, and operational KPIs at a glance.

---

## 🚀 Project Overview
This is my **first Power BI project** showcasing clean UI/UX, interactive visuals, and dynamic calculations using **DAX**. The dashboard presents financials, membership breakdowns, monthly trends, and client progress — designed for rapid decision-making.

---

## ✨ Key Features
🔹Compact, modern, dark-themed UI optimized for readability  
🔹KPIs: Revenue, Expenses, Profit, Active/Expired Memberships  
🔹Membership tier overview (Platinum / Gold / Silver) with quick stats  
🔹Monthly members and trend analysis (bar & line charts)  
🔹Client membership table with status and progress bars  
🔹Custom DAX measures and SVG progress bar for visuals  
🔹Responsive layout for presentation screens

---

## 🧰 Tech Stack
🔹**Platform:** Power BI Desktop  
🔹**Language:** DAX (Data Analysis Expressions)  
🔹**Assets:** Custom SVG elements for progress visualization, PNG hero image

---

## 📌 Example DAX (SVG Progress Bar)
This DAX measure produces an SVG progress bar used in a card/visual:

```DAX
SVG_BarChart1 =
VAR ProgressValue = [ProgressPercent]      -- Replace with your measure
VAR BarWidth = 260
VAR ProgressWidth = BarWidth * (ProgressValue / 100)
VAR select_Color = "RED"

VAR SVG_Date_URL = "data:image/svg+xml;utf8,"
VAR SVG =
    "<svg width='400' height='40' xmlns='http://www.w3.org/2000/svg'>" &
        "<rect x='10' y='10' width='" & BarWidth & "' height='20' rx='10' ry='10' fill='#555' />" &
        "<rect x='10' y='10' width='" & ProgressWidth & "' height='20' rx='10' ry='10' fill='" & select_Color & "' />" &
        "<text x='360' y='25' font-family='Arial' font-size='25' font-weight='bold' fill='white' text-anchor='end' alignment-baseline='middle'>" &
            ROUND(ProgressValue,0) & "%" &
        "</text>" &
    "</svg>"

RETURN
SVG_Date_URL & SVG
 
