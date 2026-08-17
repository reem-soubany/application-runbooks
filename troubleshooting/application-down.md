# Application Down - Troubleshooting Runbook

## Purpose

Steps to follow when an application is down or users are unable to access it.

## Before Troubleshooting

* Confirm if the issue is affecting one user or multiple users
* Check if the application works from another computer
* Check if the issue is happening in Production or Test
* Check for any scheduled maintenance
* Check if there were any recent changes to the application or server

## Troubleshooting

### 1. Check Connectivity

Make sure the user can reach the application server.

Check:

* Network connection
* VPN connection if required
* DNS
* Required ports
* Firewall rules

For a quick connectivity test you can use:

`Test-NetConnection <server> -Port <port>`

If the connection fails, determine if the issue is with the application or the network before continuing.

### 2. Check Application Services

Log into the application server & check that the required services are running.

If a service is stopped:

1. Check when it stopped
2. Review recent changes
3. Restart the service if approved
4. Test the application again

### 3. Check Authentication

If the application loads but users cannot log in check:

* User account status
* Active Directory / Entra ID
* Group membership
* Application roles
* Recent password changes
* Authentication configuration

### 4. Check Dependencies

Check any systems the application depends on.

Examples:

* Database
* File share
* API
* SMTP
* Identity provider
* Other applications

A dependency being unavailable can make the main application appear to be down.

### 5. Check Logs

Review the application and Windows logs around the time the issue started.

Look for:

* Errors
* Failed connections
* Authentication failures
* Service failures
* Configuration changes

Record the error message and timestamp if the issue needs to be escalated.

## Escalation

Escalate the issue if it requires changes outside of the application support scope.

Include:

* Application
* Environment
* Time the issue started
* Number of affected users
* Error message
* Troubleshooting already completed
* Relevant logs
* Recent changes

## After the Issue Is Resolved

* Confirm the application is accessible
* Test login
* Test the affected function
* Confirm with the user if needed
* Document the cause
* Document the fix
* Note any follow-up work
