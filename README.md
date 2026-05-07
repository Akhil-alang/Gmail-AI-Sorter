# Gmail AI Sorter using n8n + Gemini

## Overview

Gmail AI Sorter is an intelligent email automation workflow built with n8n and Google Gemini AI.

The workflow automatically:

* Reads incoming Gmail emails
* Uses AI to understand email intent
* Categorizes emails into:

  * Meeting
  * CheckLater
  * JobVacancy
* Applies Gmail labels automatically

This project helps organize inboxes efficiently using AI-powered workflow automation.

---

# Features

## AI Email Classification

Uses Google Gemini AI to analyze:

* Subject
* Email body
* Intent
* Context

---

## Automatic Gmail Labeling

Automatically adds labels:

* Meeting
* CheckLater
* JobVacancy

---

## Real-Time Automation

The workflow runs automatically whenever a new email arrives.

---

## No Coding Required

Built completely using:

* n8n
* Gmail API
* Gemini API

---

# Workflow Architecture

```text
Gmail Trigger
      ↓
Basic LLM Chain
      ↓
Gemini AI Model
      ↓
Switch Node
 ┌────────┼─────────┐
 ↓        ↓         ↓
Meeting  CheckLater JobVacancy
 ↓        ↓         ↓
Gmail    Gmail     Gmail
Label    Label     Label
```

---

# Tech Stack

| Technology    | Purpose             |
| ------------- | ------------------- |
| n8n           | Workflow Automation |
| Gmail API     | Email Access        |
| Google Gemini | AI Classification   |
| Switch Node   | Routing Logic       |
| Gmail Labels  | Email Organization  |

---

# Project Structure

```text
project/
│
├── Gmail Trigger
├── Basic LLM Chain
├── Gemini Model
├── Switch Node
├── Meeting Label Node
├── CheckLater Label Node
└── JobVacancy Label Node
```

---

# Prerequisites

Before running the workflow, ensure you have:

* Gmail account
* n8n installed
* Gemini API key
* Gmail labels created

---

# Setup Guide

## 1. Create Gmail Labels

Inside Gmail create these labels:

```text
Meeting
CheckLater
JobVacancy
```

---

## 2. Install n8n

Official Website:

urln8n[https://n8n.io](https://n8n.io)

---

## 3. Create Gemini API Key

Open:

urlGoogle AI Studio[https://aistudio.google.com/](https://aistudio.google.com/)

Generate API key.

---

## 4. Configure Gmail Trigger

Settings:

| Field     | Value   |
| --------- | ------- |
| Resource  | Message |
| Operation | Watch   |
| Label     | INBOX   |

---

## 5. Configure AI Prompt

```text
You are an email classifier.

Classify the email into ONLY one category:

- Meeting
- CheckLater
- JobVacancy

Return ONLY one word.

Email Subject:
{{ $json.subject }}

Email Body:
{{ $json.textPlain }}
```

---

# Switch Routing Rules

| Output | Category   |
| ------ | ---------- |
| 0      | Meeting    |
| 1      | CheckLater |
| 2      | JobVacancy |

Expression:

```jav
```
