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

**Check the network:**
* Open Command Prompt and run: `ping <server-name>`

**Check DNS:**
* Run: `nslookup <server-name>`
* Make sure the server name returns an IP address.

**Check the application port:**
* Open PowerShell and run: `Test-NetConnection <server-name> -Port <port>`
  * For example: `Test-NetConnection appserver01 -Port 443`
* Look for: `TcpTestSucceeded : True`
  * If it shows `False`, there may be a network or firewall issue.
* If VPN is required, make sure the user is connected before testing.

### 2. Check Application Services

Log into the application server & check that the required services are running.

If a service is stopped:

* Check when it stopped
* Review recent changes
* Restart the service
* Test the application again

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

1. Press Windows + R
2. Enter eventvwr
3. Expand Windows Logs
4. Select Application
5. Check for errors or warnings around time issue started
6. Check system for service or server-related errors
7. Open the event & record the error message, event ID & timestamp

List of what to look for:

* Errors
* Failed connections
* Authentication failures
* Service failures
* Configuration changes

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
* Confirm with the user
* Document the cause& the fix
* Note any follow-up work
