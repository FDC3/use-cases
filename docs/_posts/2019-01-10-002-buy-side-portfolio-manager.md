---
title:  "Use Case 2: Buy side Portfolio Manager"
status: ACCEPTED
layout: use_case
---

### Preconditions
On their desktop, this user has:
- An installed full-service market data terminal with news, quotes, research management, etc. The application is open and FDC3 compatible.
- A third-party portfolio management system. The application is closed and not FDC3 compatible.
- An installed application for the chat tool used by the firm. The application is open and FDC3 compatible. It also has a proprietary integration to the portfolio management system.
- The default web browser for the OS.
- The default mail application for the OS.

On their mobile device, this user has:
- The default mail application for the device.
- The default web browser for the device.
- The installed application from the market data provider.
- The installed application for the chat tool used at the firm.

### Workflow 1 (non-desktop)
While using the mobile device (out of office), the user receives an email alert from his market data provider that a new research report has been posted which mentions a company that user is interested in. The user wants to read the report and clicks on the link in the email report. The market data application is launched and shows the research report.

- Not currently supported by FDC3. Question for the API WG - https://github.com/FDC3/API/issues/52

### Workflow 2
Back in the office, the user wants to follow up on the report so he goes to his email client, finds the email and clicks the link. The market data application on the desktop displays the research report.

- Related to Workflow 1 above but more options exist on desktop.

### Workflow 3
While reading the report the user wants to look up what the firm’s internal analysts have written about the company. The user hovers over the company identifier in the report and launches a tool within the terminal that shows the firm's internal research. A note from one analyst is intriguing so the user wants to know more. The user hovers over the name and launches the chat tool with a conversation with the analyst in focus and some details regarding the note is already posted to the chat.

- Supported by Find Intents by Context, viewAnalysis and startChat
- Types sent throuh payload et fdc3.contact, fdc3.instrument, fdc3.phrase in order to pass message through the startChat intent
- Posting message automatically is not currently supported. User would have to send the message within the chat application.

### Workflow 4
During the chat, the analyst sends a link to a web site containing some further details regarding the company and the reason for the note posted. The user clicks on the link and the web browser opens. The user reads the article and continues to chat with the analyst.

- Achieved through URLs

### Workflow 5
During the chat, the analyst shares a chart with some important observations highlighted. The user clicks on the chart image in the chat and the terminal opens a live version of the chart with the observations highlighted.

 - Sharing HTML chart details through protocol handler (URI). See Workflow 1 and 2 above.

### Workflow 6
During the chat, the user realizes that some changes should be done to their holdings in the company so hovers over the company identifier and launches the portfolio management system. While looking over the holdings the user also wants to contact the firm’s trader who is listed within the system. The user hovers over the name and launches the chat tool with a conversation with the trader in focus.

- Context lookup by type to find intent
- Context types passed eg. fdc3.instrument, fdc3.contact - composite object of instrument and chat contact to send to the portfolio management system
- Context lookup typ type eg fds.contact

### Interoperability Points
- API
- Intents
- Context
- Financial Objects Program
- _Missing Overall: Protocol Handler (URI)_
