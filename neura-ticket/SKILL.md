---
name: neura-ticket
description: |
  Create Jira Service Management tickets for Neura Robotics Customer Service & Support Portal.
  Covers 4 product groups: Robot Arms, Mobile Manipulation (MAV/MAV+), MiPA, Academy & Training.
  Use when the user wants to "write a ticket", "create a ticket", "submit a ticket", or "raise a ticket"
  for any Neura Robotics support request type.
---

# Neura Robotics Ticket Creator

When user asks to write / create a ticket for Neura, do:

1. **Determine the product group** — Ask or infer from context: Robot Arms, Mobile Manipulation MAV/MAV+, MiPA, or Academy & Training.

2. **Determine the request type** — Each group supports different types:
   - **Robot Arms** & **Mobile Manipulation**: Service Request, General Inquiry, Submit a feature request
   - **MiPA**: Technical Feedback - MiPA, Service Request
   - **Academy & Training**: Book a Customer Training, Sales Training Request

3. **Collect fields** — Use the reference at `references/api_reference.md` for the exact field definitions per type. Ask only for info not yet known from conversation.

4. **Output the ticket** in a clean Markdown format matching the reference structure.
   - Use the exact field names from the portal.
   - Mark required fields with `*`.
   - Include combobox options when known (e.g. Priority, Request category).
   - Provide the portal link so the user can submit manually.

5. **DO NOT submit the ticket programmatically** — Codex only generates the ticket
   content and provides the portal link. The user must manually open the link and
   submit the ticket themselves through the Jira portal. Never fill out the portal
   form or click Send on behalf of the user.

6. **Ticket format**:
   ```
   # Ticket: <summary>

   **Product Group:** <group>
   **Request Type:** <type>

   ---

   ## Summary
   <concise summary>

   ## Description
   <detailed description>

   ## Fields

   | # | Field | Value |
   |---|-------|-------|
   | 1 | Summary* | ... |
   | 2 | ... | ... |

   *(only include fields that have values)*

   ## Priority: <priority>
   ```

   Service Request and General Inquiry have many fields — present only the populated ones rather than the full table.

7. If user needs the direct Jira portal link, construct:
   - `https://neurarobotics.atlassian.net/servicedesk/customer/portal/10/group/<group-id>/create/<request-type-id>`
   - Group IDs: Robot Arms=52, MAV/MAV+=1108, MiPA=1143, Academy=1107
   - Request type IDs: see reference
