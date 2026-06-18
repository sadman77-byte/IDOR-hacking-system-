# IDOR Vulnerability Demonstration - O'Reilly Learning Platform

## Project Overview
This repository documents the **manual discovery and exploitation of an Insecure Direct Object Reference (IDOR)** vulnerability on O'Reilly's learning platform (`learning.oreilly.com`). 

**Purpose**: Educational documentation for cybersecurity studies, understanding Broken Access Control, and quiz preparation.

**Note**: This was done as part of academic learning under instructor guidance.

---

## Vulnerability Information

- **Vulnerability Type**: Insecure Direct Object Reference (IDOR)
- **Severity**: Medium-High
- **OWASP Category**: A01:2021 - Broken Access Control
- **Platform**: O'Reilly Learning (learning.oreilly.com)

---

## Step-by-Step Process

### 1. Initial Shared Link
Received a partial link from a chat:

```
https://www.oreilly.com/videos/introduction-to-cybersecurity/390420BCRV-XXXX/
```

(Last part was redacted)

### 2. URL Manipulation (IDOR Exploitation)
- Modified the resource ID at the end of the URL.
- Guessed/completed the correct ID.
- Successfully accessed the full premium course without subscription.

**Successful URL**:
`https://www.oreilly.com/videos/introduction-to-cybersecurity/390420BCRV-[CorrectID]/`

### 3. Access Gained
- Course Title: **Introduction to Cybersecurity** by **Jeff Minakata**
- Publisher: EC-Council
- Full video player with transcript
- Course progress and chapter list visible
- Multiple modules accessible (Physical Security, Securing Operating Systems, etc.)

*(Screenshots attached in the repository showing the 404 error, successful course page, video transcript, and chapter list)*

---

## Technical Analysis

**Root Cause**:
- The application directly uses object references (course/video IDs) in the URL.
- Missing server-side authorization check to verify whether the user has valid access to that specific resource.
- Predictable ID format allowed easy enumeration and access.

**Impact**:
- Unauthorized access to premium paid content.
- Possible large-scale content enumeration.

---

## Screenshots

1. **404 Error** – When wrong ID was used.
2. **Chat Link** – Original shared link with redacted ID.
3. **Successful Course Page** – Full access gained.
4. **Video Player & Transcript** – Showing content playback.
5. **Chapter List** – Complete course modules.
6. **Instructor Search** – Jeff Minakata.

*(All screenshots are included in the `/screenshots` folder)*

---

## Lessons Learned

- Never rely solely on client-side URL parameters for authorization.
- Always validate resource ownership on the server.
- Use strong, unpredictable identifiers (e.g., UUID) when necessary.
- Implement proper access control mechanisms.

---

## Ethical & Legal Note

- This activity was performed **purely for educational purposes** and quiz preparation.
- No content was downloaded, shared, or distributed.
- Conducted under instructor guidance for learning Broken Access Control.
- Real-world exploitation without permission violates platform Terms of Service.

---

## Recommendations

**For Developers:**
- Implement `user_has_access(resource_id)` checks on every request.
- Use Role-Based or Attribute-Based Access Control.
- Rate limit ID enumeration attempts.
- Monitor abnormal access patterns.

**For Students:**
- Practice IDOR in legal labs: Try campus labs, TryHackMe, PortSwigger Web Academy, OWASP Juice Shop.
- Focus on understanding the concept rather than real platform exploitation.

---

## Tools Used
- Mobile Browser
- Manual URL editing
- Observation & Trial-and-Error

---

## References
- OWASP Top 10 2021 – Broken Access Control
- TryHackMe IDOR Rooms
- PortSwigger Academy – Access Control

---

**Disclaimer**: This repository is for **educational and research purposes only**. The author does not promote or encourage unauthorized access to any system.

---

**Author**: SADMAN ISHRAQ   
**Date**: June 2026  
**Purpose**: Academic Documentation & Quiz Preparation
