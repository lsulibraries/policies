# LDL Support - Documentation

## Roles

* Support Desk Manager
	* Manages the LDL Support board  
	* Responds to issues and interfaces with the ticket creator   
	* Categorizes and prioritizes ticket  
	* Assigns tickets to teams or individuals
	* Creates tickets in JIRA to assign to dev team. Links to cards  

* Collection management/Metadata team
	* Handles issues with collection management and metadata
	* Creates user accounts, and is primary liaison with collection administrators  
	* Primarily Scott and Cara

* Dev team
	* Responds to issues primarily through problem reports or bugs filed in JIRA

* *The following headers refer to the columns on the LDL Support Trello Board*

## About New Issues

* Newly reported issues land in this column.
* An authenticated user at the LDL can access a form to submit issues directly from the LDL. 
	* A Trello card is created and appears in this column. 
	* Some helpful fields are automatically populated from the form.
		* Referer: The URL that the form button was clicked from.
		* User Agent: Information about the browser
		* Username: The LDL (Drupal) username of the person reporting the issue. **Note that this is not the same username as the person's Trello account.**
* Users are not automatically notified when any action is taken on a card. If they are not a member of the board, then they must be notified separately, either by email, Slack, etc. For this reason, it is best if the user is added to the board.
* A due date is assigned that is 24 hours after the issue is opened. An initial response is required within that period.
	* **When an issue is acknowledged, it is moved into First Response/Triage column.**
* Only issues that have not been responded to should be in this column.
* An acknowledgement of receipt can be as simple as "I'm looking into this", but can be more complex. 
* Once first response is complete, move to Triage column.

## Triage

* An intitial response has been made to the issue reporter.
* Check to see if it has a known solution, workaround or if it's a known error.  
* Issue needs to be analyzed before assigning.
	* Attempt to understand the issue.
		* Clarify wording
		* Attempt to reproduce the issue.
		* Test
		* Concentrate on the observed behavior/the problem's symptoms  
* Categorize the issue.
    * Collection Management/Metadata
        * route to Cara/Scott
        * (Ex. Change metadata)
    * Search
        * (Ex. Unexpected search result)
    * Display/Theme
        * Ex. Button displaying wrong
    * Network/Infrastructure
        * Ex. Site is down, unresponsive
    * Feature request
        * Request for something that adds new functionality
* Prioritize the issue.
	* Prioritize according to urgency and impact
	* Urgency
        * High
            * Issue worsens or causes other problems over time rapidly
            * The blocked work is highly time sensitive - has near deadline
        * Medium
            * Issue worsens or causes other problems over time moderately or slowly
            * The blocked work is somewhat time sensitive
        * Low
            * Issue doesn't become worse over time
            * The blocked work is not time sensitive
    * Impact
        * High
            * Large number of staff are affected and cannot do their job
            * Large number of customers are affected
                * Acutely disadvantaged in some way
            * Financial or legal impact is large
            * The damage to the reputation of the site is high
        * Medium
            * A moderate number of staff are affected and cannot do their job properly
            * A moderate number of customers are affected 
                * Inconvenienced
            * Moderate financial or legal impact
        * Low
            * Minimal number of staff or site visitors affected
                * Acceptable service that requires extra effort on their part
    * Priority
        * Critical
            * High urgency and high impact
                * Start work immediately
                * Needs to be resolved ASAP
                * All hands on deck
                * Target resolution - 1 hour
        * High
            * High/medium or Medium/high
                * Escalate
                * Start work ASAP
                * Target resolution - 4 hours
        * Medium
            * Medium/medium or High/Low
                * Target resolution - 1 day
        * Low
            * Medium/low or Low/Medium
                * Target resolution - 1 week
        * Very low
            * Low/Low
                * Target resolution - 1 month
* After clarifying the issue and categorizing, the issue can be assigned

## Assign to Collection Management/Metadata

* For issues related to collection management or metadata
* For Scott and Cara to look at. Add them to the card.

## Assign to Devs

* Issues not related to collection management or metadata or third parties are assigned to devs
* Add devs to the card  
* The issue should be able to be converted into a JIRA issue at this point, which is linked to the card

## Waiting/On Hold  

* Waiting on a response from a vendor, third party, or confirming the fix with the issue creator  
* Issues assigned to a third party go here  
* Issues related to future development do not go here  

### References

[ITIL Incident Management](https://wiki.en.it-processmaps.com/index.php/Incident_Management)
[ITIL Checklist Incident Priority](https://wiki.en.it-processmaps.com/index.php/Checklist_Incident_Priority)
[Incident Management vs Problem Management](https://www.bmc.com/blogs/incident-management-vs-problem-management-whats-the-difference/)
