# Cisco Secure Endpoint - Run Orbital Query on Specified Events

# Use Case

This workflow will run Orbital Forensics snapshot Query on an endpoint where Secure Endpoint Threat Detected Event was seen.

## Installation

### Requirements

* The following system atomics are used by this workflow:
        Secure Endpoint - Get Events
        Orbital - Query - Run Query
        Webex - Post Message to Room


* The following atomic actions must be imported before you can import this workflow:
        ServiceNow - Create Incident (CiscoSecurity_Atomics)
        Service Now - Add Work Note to Incident (CiscoSecurity_Atomics)
* The targets and account keys listed at the bottom of the page

### System Targets
Target Group: `Default TargetGroup`

| Target Name | Type | Notes |
|:------------|:-----|:------|
| Secure Endpoint | HTTP Endpoint | Created with integration |
| Email | SMTP Endpoint | Created with integration |
| Webex | HTTP Endpoint | Created with integration |
| Orbital | HTTP Endpoint | Created with integration |

## Configuration

1. Add your Webex Bot API Token to the `Webex Bot Token` global variable.
1. Configure Email SMTP Target according to [documentation](https://docs.xdr.security.cisco.com/Content/Automate/targets-smtp.htm).
1. Set the `Event Types` local variable to the IDs of the event types you want the workflow to process. You can refer to the table for event types IDs.
1. Set the `Webex Room ID` local variable to the value you want the workflow to process. To find out Webex Room ID, you can add RoomID bot to your webex room.
1. By default, this workflow will not run automatically. Enable the [Automation Rule](https://docs.xdr.security.cisco.com/Content/Automate/automation-rules.htm) for the workflow to be triggered every 5 minutes.

## Usage

### Workflow steps

1.    Get a list of events and fetch all unique computer IDs
1.    Check if events were found:
- If not, end the workflow
- If so, loop through each computer:
    - Run Orbital Forensics Snapshot Query
    - Fetch Query ID
    - Send Webex message with the link to query results
    - Send Email

## Links to DevNet Learning Labs

For more information about working with Cisco XDR Automate, please visit the following [DevNet Learning Lab](https://developer.cisco.com/learning/tracks/cisco-xdr/).

## Notes

Please test this properly before implementing in a production environment. This is a sample workflow!

## Author

Oxana Sannikova (osanniko@cisco.com)