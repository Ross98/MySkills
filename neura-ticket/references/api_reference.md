# Neura Robotics Ticket Portal Reference

Portal: `https://neurarobotics.atlassian.net/servicedesk/customer/portal/10`

---

## Product Groups & Request Types

| Group | Group ID | Request Types | Type IDs |
|-------|----------|--------------|----------|
| Robot Arms | 52 | Service Request, General Inquiry, Submit a feature request | 211, 257, 3386 |
| Mobile Manipulation - MAV/MAV+ | 1108 | Service Request, General Inquiry, Submit a feature request | (same as Robot Arms) |
| MiPA | 1143 | Technical Feedback - MiPA, Service Request | 3485, 211 |
| Academy & Training | 1107 | Book a Customer Training, Sales Training Request | 3018, 2985 |

---

## Service Request – Software or Hardware Support

**Applies to:** Robot Arms, Mobile Manipulation, MiPA  
**Description:** Report any software or hardware-related issues with your NEURA system.

### Fields

| # | Field | Type | Required | Notes |
|---|-------|------|----------|-------|
| 1 | Summary* | text | yes | Include Warn/Error message if available |
| 2 | Description* | rich text | yes | What you see, when it happens, what you tried; attach screenshots/logs |
| 3 | Type of Product:* | combobox | yes | LARA |
| 4 | Affected part of the product:* | combobox | yes | Robot / System, Control Box, Teach Pendant, etc. |
| 5 | Enter the serial number of the system:* | text | yes | e.g. NR227064, NR115921, 101002804; include type label photo |
| 6 | Enter the serial number of the teach pendant:* | text | yes | e.g. 09976821; enter n/a if not applicable |
| 7 | Software Version* | text | yes | e.g. V5.1.88, v4.22.11 (from Info in top right) |
| 8 | GUI Version* | text | yes | e.g. V2.15.3 (from Info) |
| 9 | AI Version* | text | yes | e.g. V3.2.1 (from Info); enter n/a if not applicable |
| 10 | Since when is the system in operation?* | date | yes | Format: DD/MMM/YY e.g. 23/Jul/26 |
| 11 | How reproducible is the problem?* | combobox | yes | Always / Intermittent / One-time / Not reproducible |
| 12 | Product location* | text | yes | Street address, house number, postal code, city |
| 13 | Priority | combobox | no | Highest / High / **Medium** / Low / Lowest / Wish |
| 14 | Upload attachments* | file | yes | Backup, pictures, videos, service report, warranty claim |
| 15 | Share with* | combobox | yes | RocStar (default) |

---

## General Inquiry

**Applies to:** Robot Arms, Mobile Manipulation  
**Description:** General questions about features, documentation, or functionality — no serial number needed.

### Fields

| # | Field | Type | Required | Notes |
|---|-------|------|----------|-------|
| 1 | Summary* | text | yes | Concise summary of the request |
| 2 | Request category* | combobox | yes | Information / Question / Documentation / Software / Version / Hardware / Part / Interface / Integration support / Application advisory / Administrative |
| 3 | Please let us know how we can assist you.* | rich text | yes | Detailed description |
| 4 | Product* | combobox | yes | Which product is affected |
| 5 | Affected Area | combobox | no | Which part/area of the robot is affected |
| 6 | Enter the serial number of the system | text | no | |
| 7 | Software Version | text | no | |
| 8 | GUI Version | text | no | |
| 9 | AI Version | text | no | |
| 10 | Product location | text | no | |
| 11 | Priority | combobox | no | Highest / High / **Medium** / Low / Lowest / Wish |
| 12 | Attachment | file | no | Backup, pictures, videos, service report, warranty claim |
| 13 | Share with* | combobox | yes | RocStar (default) |

---

## Submit a feature request

**Applies to:** Robot Arms, Mobile Manipulation  
**Description:** Share ideas to help shape the next generation of NEURA software.

### Fields

| # | Field | Type | Required | Notes |
|---|-------|------|----------|-------|
| 1 | Share with* | combobox | yes | RocStar (default) |

Feature description is captured in the initial request type selection — no additional form fields on the create page.

---

## Technical Feedback - MiPA

**Applies to:** MiPA only  
**Description:** Provide technical feedback for MiPA.

### Fields

| # | Field | Type | Required | Notes |
|---|-------|------|----------|-------|
| 1 | Summary* | text | yes | |
| 2 | Problem Description* | rich text | yes | Detailed description of the issue |
| 3 | Serial number* | text | yes | |
| 4 | Screenshot of rqt_robot_monitor + Other Attachments* | file | yes | Required: rqt_robot_monitor screenshot, plus any other relevant files |
| 5 | Share with* | combobox | yes | RocStar (default) |

---

## Book a Customer Training

**Applies to:** Academy & Training  
**Description:** Schedule a training session.

### Fields

| # | Field | Type | Required | Notes |
|---|-------|------|----------|-------|
| 1 | Enter Company name here* | text | yes | |
| 2 | Share with* | combobox | yes | RocStar (default) |
| 3 | Number of participants | combobox | no | Default: 1; adding participants shows Full Name*, Email Address*, Role/Position* per person |
| 4 | Order Confirmation Number (OC No.)* | text | yes | e.g. OCXX-XXXXX |
| 5 | Preferred Training Date – Option 1* | date | yes | Format: M/D/YYYY; trainings held Tue-Thu, min 2 weeks lead time |
| 6 | Preferred Training Date – Option 2* | date | yes | Alternative date |
| 7 | Preferred Training Date – Option 3* | date | yes | Additional alternative |
| 8 | Comments | rich text | no | Additional details or special requirements |

---

## Sales Training Request

**Applies to:** Academy & Training (internal use only)  
**Description:** For internal use only.

### Fields

| # | Field | Type | Required | Notes |
|---|-------|------|----------|-------|
| 1 | Enter Company name here* | text | yes | |
| 2 | Share with* | combobox | yes | RocStar (default) |
| 3 | Order Confirmation Number (OC No.) | text | no | Fill after OC is created |
| 4 | Training booked by* | text | yes | Customer first and last name |
| 5 | Training format* | radio | yes | Onsite (NEURA) / Online |
| 6 | Language* | radio | yes | German / English |
| 7 | Number of participants* | text | yes | |
| 8 | Participants roles* | checkbox | yes | Operator / Software engineer / Application Engineer(Software) / Project Manager / Field engineer / Researcher / Intern / Bachelor or Master Student / Other |
| 9 | Additional Information | rich text | no | e.g. specific audience |
| 10 | Years of experience in robotics* | checkbox | yes | No experience / 0-1 year / 1-3 years / 3-5 years / 5+ years |
| 11 | Have you already worked with NEURA Robotics robots?* | radio | yes | Yes / No |
| 12 | Current challenges* | checkbox | yes | Lack of internal knowledge / Frequent malfunctions / None / Other |
| 13 | Model* | checkbox | yes | LARA / MAiRA / MAV / MAV+ / None |
| 14 | Gripper* | checkbox | yes | Mechanical / Vacuum / Magnetic / Soft / Other |
| 15 | Gripper Manufacturer / Type* | text | yes | |
| 16 | Planned applications* | checkbox | yes | Handling/Pick & Place / Gluing / Welding / Palletizing / Machine tending / Quality inspection / Assembly / Other |
| 17 | Describe application use case* | rich text | yes | |
| 18 | Training Type* | radio | yes | LARA / MAiRA / MAV |
| 19 | Comments | rich text | no | Additional requirements |


## Combobox Option Reference

### Priority
`Highest` / `High` / `Medium` (default) / `Low` / `Lowest` / `Wish`

### Request Category (General Inquiry)
`Information / Question` / `Documentation` / `Software / Version` / `Hardware / Part` / `Interface / Integration support` / `Application advisory` / `Administrative`

### How reproducible (Service Request)
`Always` / `Intermittent` / `One-time` / `Not reproducible`

### Share with
`RocStar` (default)

### Type of Product
`LARA`
