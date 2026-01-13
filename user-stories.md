# User Stories

## Story #1: Employee is on the booking screen and needs to book the conference room based on the date and time

**As an** Employee
**I want to** book a conference room for a specific date and time
**So that** I can secure the space exclusively for my meeting
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
5
### Priority:
High
### Dependencies:
- None
### Technical Notes:
- Booking conflicts should be detected using time-range overlap logic, not exact start/end matches
### Design Notes:
- Disable or visually gray out past dates in the date picker
- Use a time picker with fixed increments to reduce invalid inputs


## Story #2: Employee is on the booking screen and wishes to book recurring meetings

**As an** Employee
**I want to** set a booking to repeat on multiple days
**So that** I save time scheduling regular meetings
### Acceptance Criteria:
- Given I am on the booking screen, When I try to make recurring bookings and one of the days selected has a booking at that time, Then return and error message in red of the specific date and time that the conflict is taking place and give options to continue with the other days or change the times altogether.
- Given I am on the booking screen, When I try to make recurring bookings into days that the office is not open, Then return an error message in red that the days selected lies on days that the office is closed and give options to select other days when the office is open.
### Story Points:
5
### Priority:
Medium
### Dependencies:
- Dependent on Story 1
### Technical Notes:
- The API should return a list of conflicted dates and time ranges, not just the first conflict
- 
### Design Notes:
- Use a clear “Recurring booking” switch button that shows more otions to select other days when enabled
- Default to days when the office is open when selecting recurrence options


## Story #3: Employee is able to filter the conference rooms based on the room capacity

**As an** Employee
**I want to** filter rooms by seating capacity
**So that** I only see rooms that fit my number of attendees.
### Acceptance Criteria:
- Given I am on the booking screen, When I select the filter button for x amount of people, Then the rooms shown should be ordered in ascending order or descending order.
- Given I am viewing the rooms, When update the capacity value, Then the list of the rooms updates without the need to refresh the page
### Story Points:
3
### Priority:
Low
### Dependencies:
- Story 1
### Technical Notes:
- Sorting the rooms in ascending/descending should immediately be applied after capacity filtering.
- Rooms that do not meet the selected capacity that has been filtred should not be disabled, but excluded.
- when there hasn't been any capacity selected, then no capacity filtering should be applied.
### Design Notes:
- Clearly label the filter
- Use a slider or numeric input for selecting the room capacity


## Story #4: Employee is able to cancel a booking that was made

**As an** Employee
**I want to** cancel my existing bookings
**So that** the room becomes available for others to use.
### Acceptance Criteria:
- Given I am on the cancellation screen, When I press the cancel button, Then the booking with the details that are tied with that specific booking is completely removed from the schedule thus freeing that time slot to be booked again without conflict.
### Story Points:
3
### Priority:
Medium
### Dependencies:
- Story 1
### Technical Notes:
- Only the creator of the booking or a role that is authorized to(e.g admin) is able to cancel the booking.
### Design Notes:
- Use a confirmation dialog to make sure that there are no accidental cancellations


## Story #5: Employee is able to to select what specific equipment is required for the room for that specific booking

**As an** Employee
**I want to** reserve specific equipment (e.g projectors, whiteboard) with my booking
**So that** the room is fully prepared for my meeting needs.
### Acceptance Criteria:
- Given I am on the booking screen, When I select a button that opens a menu to select any additional equipment, Then an additional menu is opened and I am able to select more equipments that i may require(e.g. more chairs).
### Story Points:
5
### Priority:
Medium
### Dependencies:
- Story 1
### Technical Notes:
- Equipment options must be sourced from a configurable master list
- Equipment availability should be validated per booking time slot where applicable.
### Design Notes:
- Use a clear “Add equipment” or “Equipment required” button on the booking screen


## Story #6: Admin is able to see a screen of the dashboard showing all of the different bookings that were made

**As an** Admin
**I want to** view a list of all active bookings
**So that** I can monitor overall room utiliztion and activity.
### Acceptance Criteria:
- Given I am logged in as Admin, When I navigate to the dashboard, Then I should see see the total number of bookings for each day
### Story Points:
5
### Priority:
High
### Dependencies:
- None
### Technical Notes:
- Access to the dashboard should be restricted to only the Admin having access using role-based access control
### Design Notes:
- Use chart based visualisation or calender style to view the information in the dashboard


## Story #7: Facilities Manager is able to schedule times when the rooms need maintenance

**As a** Facilities Manager
**I want to** book specific rooms for maintenance
**So that** users are prevented from booking rooms undergoing repairs.
### Acceptance Criteria:
- Given I am logged in as Facilities Managers, When I choose a specific room and select "Schedule Maintenance", Then I can schedule a maintenance for specific dates and times
- Given I am logged in as Facilities Managers, When I try to schedule maintenance during a time a room is booked, Then an error should be shown in red stating that the room is booked at that time-slot.
### Story Points:
5
### Priority:
High
### Dependencies:
- None
### Technical Notes:
- Access to the room maintenance scheduling should be restricted to the role of Facilities Manager using role-based access control
- Maintenance must block room availability in the same way as if a room has been booked.
### Design Notes:
- Clearly show that scheduling maintenance will block room availability.
- Show the existing bookings on a timeline or calendar


## Story #8: Receptionist is able to assist visitors with bookings

**As a** Receptionist
**I want to** book rooms on behalf of external visitors
**So that** guests without system access can still secure a meeting space
### Acceptance Criteria:
- Given a guest arrives and needs a room booked, When I as the receptionist select an option to book on behalf of a guest, Then I can see which rooms are available
- Given I have selected the room to book, When I begin booking, Then I have to specify who the room is for and how long the room will be booked for and the purpose of booking the room.
### Story Points:
5
### Priority:
High
### Dependencies:
- story 1
### Technical Notes:
- Have a "Receptionist" role that has limited access and is able to book the conference room on behalf of others.
### Design Notes:
- Have a receptionist dashboard that has an option to book for visitors


## Story #9: Admin is able to resolve issues arising from booking conflicts

**As an** Admin
**I want to** cancel a user's booking manually
**So that** I can free up space for urgent executive needs or emergencies.
### Acceptance Criteria:
- Given I am logged in as Admin, When I access the dashboard, Then I should see a section named "conflics" which I can navigate to in order to view all the different conflicts that have risen.
- Given the system is runnung normally, When a user attempts to double book a certain time-frame, Then the system should detect the conflict and prevent the booking.
### Story Points:
3
### Priority:
Medium
### Dependencies:
- story 1
- story 6
### Technical Notes:
- Push conflicts that arise to the admin dashboard from them to resolve.
- Notify the admin that a conflict a been detected.
### Design Notes:
- Button on the dashboard to navigate to the conflicts section


## Story #10: Admin is generating different user reports
**As an** Admin
**I want to** generate user report on conference room usage
**So that** so I can optimise space allocation and analyse patterns of how often the room was utilized.
### Acceptance Criteria:
- Given Logged in as Admin, When I navigate to reports section on the admin dashboard, Then I should see options to represent the data in different formats(e.g peak hours, popular rooms)
- Given I want to understand when rooms are most in demand, When I select the peak hours report for over the past month, Then I should receive reports showing the most popular hours that rooms get booked.
### Story Points:
5
### Priority:
Medium
### Dependencies:
- story 1
- story 6
### Technical Notes:
- Restrict personal user data to Admins only
### Design Notes:

- Have a button to navigate to the reports section
