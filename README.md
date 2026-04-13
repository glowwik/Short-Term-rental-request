# Volvo Financial Services – Short Term Rental (STR) Approval Flow

## Project Overview

This project automates the **Short-Term Rental (under 12 months) request and approval process** for Volvo Financial Services. Built on **SharePoint Lists** and **Power Automate Flows**, it eliminates manual email follow-ups, centralizes credit assessments, and enforces a clear voting workflow.

## Business Problem

- Renault team submits rental requests via a form  
- Credit team manually tracked requests, leading to delays and missed emails  
- No structured voting or approval logging  
- Frequent back-and-forth for missing information  

## Solution

A SharePoint list acts as the system of record. Three automated flows handle:

1. **New request notification** – alerts credit team instantly  
2. **Voting & decision engine** – supports 1‑vote, 2‑vote, decline, and “need more info” scenarios  
3. **AML check** – automatically returns an AML score based on NACE code  

## Key Features

-  Auto‑emails at every stage (no manual outreach)  
- Voting logic with expiry date enforcement  
- Conditional paths:  
  - Single analyst approval  
  - Two‑voter approval (with optional conditions)  
  - Decline (requires 2 votes)  
  - Request more information  
     Decision and expiry dates auto‑populated  
-  Clean audit trail inside SharePoint  

## Technologies Used

| Tool | Purpose |
|------|---------|
| SharePoint Lists | Central data storage |
| Power Automate (Flow) | Workflow & email automation |
| Microsoft Forms | Intake form for Renault team |
| Microsoft Teams | Voting notifications |

## My Role

- **Process owner & designer**  
- Mapped the entire flow from request to decision  
- Configured SharePoint list columns and choice fields  
- Built and tested 3 automated flows  
- Created this documentation guide for team handover  

## Files in This Repository

| File | Description |
|------|-------------|
| <img width="582" height="674" alt="image" src="https://github.com/user-attachments/assets/e853c96b-80c0-4b33-9395-06f55516f18c" /> | Power Automate flows - When an item is created  |
| <img width="746" height="947" alt="image" src="https://github.com/user-attachments/assets/5ead0cf9-a5ea-4d38-b8c2-a8d16104f3bd" /> | Power Automate flows - When an item is modified |
| <img width="552" height="292" alt="image" src="https://github.com/user-attachments/assets/91dead93-ced4-4479-b778-922995f163ab" />| Step that stops from infinite trigger loop |
| <img width="539" height="936" alt="image" src="https://github.com/user-attachments/assets/43160ae4-8717-415e-8290-848c0d18af67" /> <img width="551" height="569" alt="image" src="https://github.com/user-attachments/assets/a0170fc5-6a12-4f60-8839-7456d160b445" /> | Anti Money Laundering - SIC Code / NACE Code checker (Flow and SharePoint List) |

| <img width="1862" height="865" alt="image" src="https://github.com/user-attachments/assets/897f8e2d-5d01-4b07-98d6-94fe0c844355" /> | SharePoint list structure (form view) |




---

## Decision Matrix 

| Scenario | AnalystVote | SecondVote | Status After | Action |
|----------|-------------|------------|--------------|--------|
| **1 vote - Approve** | Approve | (empty) | Approved | Auto-fill dates + send approval email |
| **1 vote - Approve w/ conditions** | Approve with conditions | (empty) | Approved | Add conditions from `AddConditions` cell |
| **1 vote - Decline** | Decline | (empty) | (not allowed) | Actually needs 2 votes per guide |
| **2 votes - Approve** | Approve | Approve | Approved | Auto-fill dates + send approval |
| **2 votes - Approve w/ conditions** | Approve with conditions | Approve with conditions | Approved | Merge conditions from both voters |
| **2 votes - Decline** | Decline | Decline | Declined | Auto-fill dates + send decline email |
| **Need more info** | Need more info | (any) | Need additional info | Email requestor with `NeedAdditionalRequested` text |

---

 

## Process Highlights 

> *“Status change is a trigger for flow – be careful and mindful of it. We want to avoid sending unnecessary/confusing emails.”*

> *“Those are auto‑emails created by flow. You don't need to do any actions outside SharePoint list – it's all done for you.”*

## Future Improvements

- Add dashboard for pending votes  
- Integrate with SAP for contract generation  
- Log SLA timestamps (request received → decision made)  



*This project was developed for Volvo Financial Services and is shared in my portfolio to demonstrate SharePoint + Power Automate process automation.*
