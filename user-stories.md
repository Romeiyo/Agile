# User Stories

## Story 1: Employee is on the booking screen and needs to book the conference room based on the date and time

**As an** Employee
**I want to** be able to book the conference room to use on a certain date at a certain time on the booking screen,
**So that** no one else is able to book it for that same time and only I am reserved it for that specific time.
### Acceptance Criteria:
#### Invalid date selected
- Given I am on the booking screen, When I try select a date from before the current date, Then those dates should be blanked out to not allow me to select them.
#### Booking conflict 
- Given I am on the booking screen, When I try to book for a date and time that is already reserved, Then return an error message in red of the conflict specifying the date and timeframe of the conflict.
#### Booking outside of office hours
- Given I am on the booking screen, When I try to book for a date and time that is outside of office hours, Then an error message in red should be returned stating that "The booking should be within office hours.".
#### Booking accepted
- Given I am on the booking screen, When I book the conference room at a date and time that's available, Then return a snackbar that the booking has been made and clear the information from the containers that it was filled into.
### Story Points:
[Choose from: 1, 2, 3, 5, 8, 13]
### Priority:
High
### Dependencies:
- None
### Technical Notes:
- Any assumptions, constraints, or technical considerations
### Design Notes:
- UI / UX considerations or edge cases
