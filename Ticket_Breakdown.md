# Ticket Breakdown
We are a staffing company whose primary purpose is to book Agents at Shifts posted by Facilities on our platform. We're working on a new feature which will generate reports for our client Facilities containing info on how many hours each Agent worked in a given quarter by summing up every Shift they worked. Currently, this is how the process works:

- Data is saved in the database in the Facilities, Agents, and Shifts tables
- A function `getShiftsByFacility` is called with the Facility's id, returning all Shifts worked that quarter, including some metadata about the Agent assigned to each
- A function `generateReport` is then called with the list of Shifts. It converts them into a PDF which can be submitted by the Facility for compliance.

## You've been asked to work on a ticket. It reads:

**Currently, the id of each Agent on the reports we generate is their internal database id. We'd like to add the ability for Facilities to save their own custom ids for each Agent they work with and use that id when generating reports for them.**


Based on the information given, break this ticket down into 2-5 individual tickets to perform. Provide as much detail for each ticket as you can, including acceptance criteria, time/effort estimates, and implementation details. Feel free to make informed guesses about any unknown details - you can't guess "wrong".


You will be graded on the level of detail in each ticket, the clarity of the execution plan within and between tickets, and the intelligibility of your language. You don't need to be a native English speaker, but please proof-read your work.

## Your Breakdown Here

I gonna make 4 tables - Agent, Shift, Facility, Book

And each table has following fields.

Agent: Id, Name, DateOfBirth
Shift: Id, WorkStart, WorkFinish, Year, Quarter
Facility: Id, Name
Book: Id, FacilityId, ShiftId, AgentId, CustomAgentId

This CustomAgentId is set when facilities book the shift with the agent.

So when `getShiftsByFacility` function is invoked, it returns the set of book data with given facility id.
It contains BookId, FacilityId, ShiftId, WorkStart, WorkFinish, Year, Quarter, AgentId, CustomAgentId.
These fields all contains the neccessary information about generating reports.

After that, when `generateReport` function is invoked, the CustomAgentId is represent instead of the AgentId which is internal database id.
