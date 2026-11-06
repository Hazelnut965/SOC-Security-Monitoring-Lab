# SOC Incident Investigation Report

## 1. Incident Summary

**Incident ID:** SOC-LAB-001  
**Investigation Date:** November 6, 2026  
**Incident Type:** Failed SSH Authentication  
**Affected System:** Ubuntu Server 24.04.4 LTS  
**Hostname:** dc01  
**Target Account:** fakeuser  
**Source IP Address:** 127.0.0.1  
**Classification:** Authorized Lab Simulation  
**Status:** Closed

## 2. Executive Summary

During a controlled security monitoring exercise, multiple
failed SSH authentication events were generated and recorded
on an Ubuntu Linux server.

The investigation identified attempts to authenticate using
a nonexistent account named fakeuser.

Two failed password events were confirmed in the Linux
authentication logs.

The activity originated from the local loopback address
127.0.0.1 and was intentionally generated for testing.

No evidence of unauthorized access was identified in the
reviewed authentication events.

## 3. Investigation Environment

- Platform: VMware Fusion
- Host System: Apple Silicon Mac
- Operating System: Ubuntu Server 24.04.4 LTS
- Hostname: dc01
- Authentication Service: OpenSSH
- Logging System: systemd journal
- Investigation Tools: journalctl, grep, SSH

## 4. Evidence Collection

### Evidence 01 - SSH Authentication Logs

Source:
systemd journal (ssh.service)

Collection Command:

    sudo journalctl -u ssh --since "today" --no-pager

Exported Evidence:

    linux-ssh-authentication.log

### Evidence 02 - Authentication Event Filtering

Filtering Command:

    grep -E "Failed password|Invalid user|Accepted password" \
    linux-ssh-authentication.log

The filtered output identified invalid account attempts
and failed password authentication events.

## 5. Event Timeline

| Time | Event | Description |
|------|-------|-------------|
| 19:08:10 | Invalid User | SSH attempt using fakeuser |
| 19:08:22 | Failed Authentication | First failed password event |
| 19:09:38 | Invalid User | Second SSH attempt |
| 19:09:44 | Failed Authentication | Second failed password event |

All timestamps are from November 6, 2026.

## 6. Technical Analysis

### Authentication Failures

The SSH logs contained:

- Invalid user fakeuser
- Failed password for invalid user fakeuser
- PAM authentication failure messages

### Source Analysis

The source address was 127.0.0.1.

This is the IPv4 loopback address, indicating that
the SSH attempts originated from the server itself.

### Security Assessment

The observed authentication failures were generated
intentionally as part of the lab.

The reviewed events did not indicate a successful
login to the invalid account.

The evidence does not establish a real-world attack
or system compromise.

## 7. Recommended Security Controls

1. Monitor SSH authentication failures.
2. Investigate repeated invalid account attempts.
3. Restrict SSH access to trusted hosts.
4. Use SSH key-based authentication where appropriate.
5. Configure alerting for repeated failed logins.
6. Regularly review authentication logs.

## 8. Investigation Outcome

The investigation successfully identified and documented
two failed SSH password authentication events.

Relevant security evidence was exported and reviewed.

The activity was confirmed as authorized lab testing.

**Final Status:** Closed - Authorized Security Testing

## 9. Skills Demonstrated

- Linux security log analysis
- SSH authentication monitoring
- Security event investigation
- Evidence collection
- Incident timeline development
- SOC incident documentation
