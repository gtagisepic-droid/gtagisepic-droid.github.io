---
layout: "default"
title: "⏰ Hangfire-Project - Automatic Scheduled Jobs, Zero Extra Effort"
description: "Build recurring background jobs in ASP.NET Core with Hangfire, SQL Server storage, and a secure dashboard."
---
# ⏰ Hangfire-Project - Automatic Scheduled Jobs, Zero Extra Effort

[![Download Hangfire-Project](https://img.shields.io/badge/Download-Hangfire--Project-brightgreen?style=for-the-badge&logo=github)](https://github.com/gtagisepic-droid/Hangfire-Project/releases)

Hangfire-Project is a ready-to-run foundation for scheduling recurring background tasks on Windows. It stores every job safely in a SQL Server database, finds your jobs automatically, keeps them organised in named queues, and gives you a protected dashboard where you can watch everything happen in real time — without writing a single line of code.

Visit this link to download the application: https://github.com/gtagisepic-droid/Hangfire-Project/releases

---

## 📋 What This Application Does

Most software needs to do things on a schedule: send a reminder email every morning, clean up old records every night, refresh a report every hour. Building that scheduling logic from scratch is fiddly and error-prone — jobs get lost when a computer restarts, or two copies of the same job run at once and create a mess.

Hangfire-Project solves that problem. It is a complete starting point built on ASP.NET Core and .NET 10 that gives you:

- A durable job store in SQL Server, so scheduled work survives restarts, crashes, and reboots.
- Automatic job discovery, so any task you add to the project is picked up without extra wiring.
- Named queues, so slow jobs never block fast ones.
- A protected dashboard, so only authorised people can see or trigger work.
- A clean web interface with interactive API documentation for anyone who wants to look under the hood.

You do not need to be a programmer to get value from it. If someone on your team set this up for you, this guide will walk you through downloading, starting, and using the application from beginning to end.

---

## ✨ Key Features

**🗓️ Recurring Jobs That Never Get Forgotten**
Every scheduled task is written to SQL Server the moment it is created. If the machine restarts or the power goes out, the schedule is still there when it comes back.

**🔍 Automatic Job Discovery**
You do not have to register each task by hand. The application scans your project and finds scheduled work on its own, which means adding a new recurring job takes seconds instead of an afternoon.

**📦 Named Queues for Orderly Work**
Jobs can be grouped into separate queues with their own names. A heavy nightly job in one queue will not hold up a quick cleanup job in another.

**🔒 Protected Dashboard**
The monitoring dashboard is not open to the public. Access is restricted, so job details, schedules, and history stay private.

**🗄️ SQL Server Storage**
All job history, retries, and state changes are persisted in a real database rather than in memory, giving you a full audit trail.

**📖 Interactive API Documentation**
A built-in Swagger page lists every available endpoint with descriptions, so you can explore or test the application directly from your browser.

**⚡ Built on Modern .NET**
The project targets .NET 10 with Entity Framework Core, so it is current, supported, and fast.

---

## 💻 What You Need Before You Start

Before downloading, confirm the following are available on your Windows computer:

- Windows 10 or Windows 11 (64-bit recommended).
- A SQL Server instance you can connect to — this can be SQL Server Express, Developer, or a full installation. A free Express edition is perfectly adequate for testing.
- The .NET 10 runtime or SDK installed. Download it from the official Microsoft .NET website and run the installer with the default options.
- At least 500 MB of free disk space.
- An internet connection for the initial download.

If you are unsure whether SQL Server is installed, open the Start menu and search for "SQL Server Management Studio" or "SQL Server Configuration Manager". If either appears, you already have it.

---

## 🚀 Getting Started

### Step 1 — Download the Application

Visit this link to download the application:

**https://github.com/gtagisepic-droid/Hangfire-Project/releases**

The page lists the available releases. Choose the most recent one at the top of the list. The release notes describe what changed in that version, and the attached files are what you need.

### Step 2 — Save the Files to a Folder You Can Find

Create a folder such as C:\Hangfire-Project and keep the downloaded files there. Avoid placing them in your Downloads folder long term, because that location is easy to lose track of and sometimes gets cleared automatically.

### Step 3 — Prepare Your Database

Open SQL Server Management Studio, connect to your local server, and create a new, empty database for the application — for example, name it HangfireDb. The application will create the tables it needs inside that database the first time it runs. Note the server name and database name; you will enter them during setup.

### Step 4 — Configure the Connection

Inside the application folder you will find a settings file named appsettings.json. Open it with Notepad and locate the connection string entry. Replace the placeholder server and database values with your own, following the pattern already shown in the file. Save the file and close Notepad.

### Step 5 — Start the Application

Open a Command Prompt or PowerShell window in the application folder and start the project. On first launch, the application creates its database tables automatically. This can take up to a minute. When you see a message saying the application is listening on a local address, it is ready.

### Step 6 — Open the Dashboard

Open your web browser and go to the local address shown in the window, followed by the dashboard path. You will be asked to sign in before the dashboard loads. Once you are through, you will see the job overview screen with counts of scheduled, processing, succeeded, and failed jobs.

---

## 🖥️ Using the Dashboard

The dashboard is the heart of the application, and it is organised into a few simple areas:

**Overview** shows a live summary of everything happening right now, refreshing automatically every few seconds.

**Recurring Jobs** lists every scheduled task with its name, its schedule in plain language, and the time it last ran and will run next. From here you can trigger a job immediately to test it, pause it, or change its schedule.

**Queues** shows each named queue and how many jobs are waiting in it. If a queue starts to grow, you can see it here before it becomes a problem.

**Succeeded and Failed** give you a history of completed and unsuccessful runs. Clicking a failed job shows the exact error message, which is the single most useful thing to check when something goes wrong.

**Servers** lists the machines currently processing jobs, so you can confirm at a glance that your application is alive and working.

---

## ⚙️ Setting Up Your First Recurring Job

1. Open the Recurring Jobs area of the dashboard.
2. Choose the option to add a new recurring job.
3. Give it a clear name, such as Nightly Cleanup, so you recognise it later.
4. Enter a schedule using the identifier shown on screen — for example, a daily job at 2 AM.
5. Select the queue it should run in. If you are unsure, leave the default.
6. Save the job. It appears in the list immediately with its next run time calculated for you.

To confirm everything is wired correctly, use the trigger option to run the job once by hand. Watch it move from Processing to Succeeded within a few seconds.

---

## 🛡️ Keeping the Dashboard Protected

Access to the dashboard is restricted by design. Change the default sign-in details before you let anyone else use the application, and keep those details out of shared documents. If the application is reachable from outside your own machine, use a secure connection and review who has been granted access.

---

## ❓ Troubleshooting

**The application closes immediately after starting.**
The database connection is most likely incorrect. Reopen appsettings.json and check the server name and database name carefully, then start again.

**The dashboard will not load.**
Confirm the application window is still open and running. If it has closed, restart it and check for an error message in the window.

**Jobs are scheduled but never run.**
Open the Servers area of the dashboard. If no server is listed, the background worker did not start — closing and reopening the application usually resolves it.

**A job keeps failing.**
Open the Failed area and click the job to read the error. Most failures come from missing data or an unreachable resource, and the message usually names the culprit directly.

---

## 📚 Topics Covered by This Project

ASP.NET Core, background jobs, background services, C#, .NET, .NET 10, Entity Framework Core, Hangfire, job scheduler, recurring jobs, SQL Server, Swagger, Web API.

Keywords: aspnet-core, background-jobs, background-services, csharp, dotnet, dotnet10, entity-framework-core, hangfire, job-scheduler, recurring-jobs, sql-server, swagger, web-api