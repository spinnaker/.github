## Spinnaker Vulnerability Handling Process
### Reporting Vulnerabilities
New vulnerability reports will be accepted only by contacting security@spinnaker.io.  This email inbox is monitored by members of the Security SIG.  As a standard SLA, we aim for responding to new vulnerability reports within 1 week of receiving the report.  Wherever possible, security@spinnaker.io should be CC’ed on all related correspondence.  

##### Standard submission form:
```

## Services impacted
list services here

## Potential level of impact
Allows attackers to read all accounts regardless of permissions

## Proof of concepts or exploits
curl <spinnaker-api>/bad/path/on/api

## Credits
Party who should receive credit OR Anonymous
```

All security tooling reports will also be forwarded to security@spinnaker.io to make sure that all security issues are consistently evaluated and documented.  
#### Evaluating New Reports
Members of the Security SIG with knowledge of affected Spinnaker services will review new reported security issues to determine:

* Is this a known issue?  If so, does it offer information we didn’t have yet?
* Does this vulnerability apply in the context of a deployed Spinnaker instance?
* What is the CVSS v3.0 score of the vulnerability in the context of our application?
* Are there exploits or proof-of-concept code to take advantage of the vulnerability?
* What services and release versions are affected by the vulnerability?

The taxonomy we are using to evaluate each vulnerability takes into account the [CVSS v3.0 score](https://nvd.nist.gov/vuln-metrics/cvss/v3-calculator) of a security issue as well as its exploitability to allow us to stay focused on addressing legitimate security risks in the Spinnaker codebase.  For clarity, we use the CVSS score to inform the rest of our evaluation process.

| Severity | Description | 
| --- | --- | 
|High |  CVSS 8.0 - 10.0 and may be readily compromised with publicly available malware or exploits.|
| Medium | CVSS 6.0 - 10.0, is not actively exploited, and no known exploit has been made publicly available. |
| Low | CVSS 0.0 - 5.9, and may be mitigated with reasonable efforts, is mitigated through other established controls, or is unable to be mitigated due to normal operations. |

During this step, a CVE ID will be reserved for new security vulnerabilities as a placeholder.

### Tracking Vulnerabilities
We will track new and existing security vulnerabilities in an issue-only private repository under the Spinnaker GitHub org.  These will be visible to and reviewed by the Security SIG.  Issues will include:
* The CVE ID of the security vulnerability
* The CVSS v3.0 score of the vulnerability
* The severity of the vulnerability against our taxonomy
* An explanation of the vulnerability and which components are impacted
* The current state of the vulnerability against the most recent release
* Justification from the Security SIG on our response to the vulnerability
* Anticipated timeline for mitigating the vulnerability

Additionally, new vulnerabilities will be tagged with the severity of the vulnerability, and the releases and microservices affected.  These private issues will be updated and reviewed by the Security SIG bi-weekly as needed, and should document roles and responsibilities, as well as evidence of our decision-making process.

### Mitigating Vulnerabilities
After a vulnerability has been evaluated and confirmed as an actual security risk to the Spinnaker community, the Security SIG will identify individuals that will develop a patch or otherwise mitigate the vulnerability.  

Work and updates should be tracked in the relevant GitHub issue.  Once a vulnerability is ready to publicly announce, the CVE record will be updated and the private GitHub issue will be copied to the Spinnaker issues page and marked as a sig-security issue. 

Notification of the CVE will be posted in slack in the #sig-security channel.  An email will also be sent to the [spinnaker announcement mailing list](https://groups.google.com/g/spinnaker-announce) with details about the CVE highlighting call to action, if any, in the subject line. The status of mitigated vulnerabilities should be included in the release notes.
