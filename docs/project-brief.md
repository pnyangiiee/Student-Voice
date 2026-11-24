# Student Voice — One-Page Project Brief

## 1. Project pitch

Student Voice is a simple digital complaint and suggestion box for a school community. It gives students a convenient way to record concerns or ideas and gives a reviewer a basic view for checking and updating the feedback status.

## 2. Community problem

Students may have concerns about classroom facilities, cleanliness, teaching and learning, student services, school activities, or campus safety. A physical suggestion box may not always be convenient, and students may feel uncomfortable identifying themselves when sharing certain feedback. The project explores a simple digital alternative that supports both anonymous and identified submissions.

This problem statement is a project proposal. The team should confirm it with actual students or school stakeholders before presenting it as a measured finding.

## 3. Target users

- **Students:** submit a complaint or suggestion, choose a category, write details, and choose whether to identify themselves.
- **School reviewer / administrator:** view saved entries, search and filter them, inspect details, and update their statuses.

## 4. Scope and features

### Included

- Complaint and suggestion submission.
- Feedback categories.
- Subject and description fields with validation.
- Anonymous or identified submission.
- Local saving with browser localStorage.
- Admin Dashboard with summary counts.
- Search, type filter, and status filter.
- Feedback detail view.
- Status options: Pending, Under Review, Resolved, and Rejected.

### Not included in this lab prototype

- Accounts, login, or role-based access.
- Cloud database or cross-device synchronization.
- Real delivery to the school administration.
- Email or push notifications.
- Attachments, replies, or public comments.

## 5. Functional requirement

**FR-01 — Student Complaint and Suggestion Submission**

The system shall allow students to submit complaints and suggestions by selecting a feedback type, category, subject, and description. Students shall have the option to submit feedback anonymously or provide their personal information.

### Acceptance criteria

1. The student can select Complaint or Suggestion.
2. The student can select a category.
3. The student must enter a subject and a description.
4. The student can choose anonymous submission.
5. When anonymous is selected, the name and student ID are not saved in the feedback record.
6. When identified submission is selected, the student's full name is required and student ID is optional.
7. The form prevents submission when required values are missing or invalid.
8. A valid submission is saved in localStorage with a reference ID, date, and Pending status.
9. The Admin Dashboard can display saved entries and update their statuses.

## 6. Proposed architecture

```text
Student Portal (index.html)
        |
        v
JavaScript form validation
        |
        v
Feedback record (JavaScript object)
        |
        v
Browser localStorage
        |
        v
Admin Dashboard (same index.html)
        |
        +--> Search and filters
        +--> View details
        +--> Update feedback status
```

## 7. Data record

Each saved record contains:

- `id`: generated feedback reference.
- `type`: Complaint or Suggestion.
- `category`: selected feedback category.
- `subject`: short feedback title.
- `description`: feedback details.
- `anonymous`: true or false.
- `studentName`: blank for anonymous submissions.
- `studentId`: blank for anonymous submissions; optional for identified submissions.
- `status`: Pending, Under Review, Resolved, or Rejected.
- `createdAt`: date and time of submission.

## 8. Success criteria for the prototype

The prototype is successful when a student can submit valid anonymous and identified feedback, the record remains after a page refresh in the same browser, and the Admin Dashboard can find the record and update its status.

## 9. Limitations and ethical note

The project uses localStorage for a classroom demonstration. It is not a secure anonymous reporting channel and does not transmit data to school officials. It should not be used for real sensitive, emergency, or confidential reports. A production system would require secure server-side storage, access control, transport security, privacy safeguards, and a clear process for handling student reports.
