# Security Incident Timeline

## Incident Overview
- Incident Type: Failed SSH Authentication
- System: Ubuntu Server 24.04.4 LTS
- Hostname: dc01
- Source IP: 127.0.0.1
- Target Account: fakeuser
- Investigation Date: November 6, 2026
- Classification: Authorized Lab Simulation

## Event Timeline

| Time | Event | Observation |
|------|-------|-------------|
| 19:08:10 | Invalid user detected | SSH login attempted for fakeuser |
| 19:08:22 | Authentication failed | Incorrect credentials rejected |
| 19:09:38 | Second invalid user event | Another SSH login attempt |
| 19:09:44 | Authentication failed | Second password failure recorded |

## Investigation Findings
- Two failed SSH password authentication events were identified.
- Both attempts targeted the nonexistent account fakeuser.
- The source IP was 127.0.0.1, indicating localhost activity.
- The events were intentionally generated for security monitoring practice.
- No evidence of unauthorized access was identified in the reviewed events.

## Recommended Security Controls
- Monitor repeated failed authentication attempts.
- Disable SSH password authentication where key-based access is configured and verified.
- Restrict SSH access to trusted systems.
- Configure alerting for repeated authentication failures.
- Regularly review authentication logs.

## Investigation Status
Closed - Authorized Security Testing
