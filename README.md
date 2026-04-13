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
| `docs/Short_Term_Rental_Process_Guide.docx` | Full user guide with screenshots |
| `flows/*.json` | Power Automate flow definitions (exported) |
| `sharepoint/list_schema.json` | SharePoint list structure |
| `screenshots/` | All images from the guide |

 

## Process Highlights 

> *“Status change is a trigger for flow – be careful and mindful of it. We want to avoid sending unnecessary/confusing emails.”*

> *“Those are auto‑emails created by flow. You don't need to do any actions outside SharePoint list – it's all done for you.”*

## Future Improvements

- Add dashboard for pending votes  
- Integrate with SAP for contract generation  
- Log SLA timestamps (request received → decision made)  



*This project was developed for Volvo Financial Services and is shared in my portfolio to demonstrate SharePoint + Power Automate process automation.*
