0x19. Postmortem
DevOpsSysAdmin

    By: Sylvain Kalache
    Weight: 1
    Project over - took place from Aug 7, 2023 6:00 AM to Aug 14, 2023 6:00 AM
    Manual QA review was done by Darlington Obioha on Aug 9, 2023 4:55 PM

In a nutshell…

    Manual QA review: 13.0/13 mandatory & 1.0/1 optional
    Altogether:  200.0%
        Mandatory: 100.0%
        Optional: 100.0%
        Calculation:  100.0% + (100.0% * 100.0%)  == 200.0%

Concepts

For this project, we expect you to look at this concept:

    On-call

Background Context

Any software system will eventually fail, and that failure can come stem from a wide range of possible factors: bugs, traffic spikes, security issues, hardware failures, natural disasters, human error… Failing is normal and failing is actually a great opportunity to learn and improve. Any great Software Engineer must learn from his/her mistakes to make sure that they won’t happen again. Failing is fine, but failing twice because of the same issue is not.

A postmortem is a tool widely used in the tech industry. After any outage, the team(s) in charge of the system will write a summary that has 2 main goals:

    To provide the rest of the company’s employees easy access to information detailing the cause of the outage. Often outages can have a huge impact on a company, so managers and executives have to understand what happened and how it will impact their work.
    And to ensure that the root cause(s) of the outage has been discovered and that measures are taken to make sure it will be fixed.

Resources

Read or watch:

    Incident Report, also referred to as a Postmortem
    The importance of an incident postmortem process
    What is an Incident Postmortem?

More Info
Manual QA Review

It is your responsibility to request a review for your postmortem from a peer before the project’s deadline. If no peers have been reviewed, you should request a review from a TA or staff member.
Tasks
0. My first postmortem
mandatory
Score: 100.0% (Checks completed: 100.0%)

Using one of the web stack debugging project issue or an outage you have personally face, write a postmortem. Most of you will never have faced an outage, so just get creative and invent your own :)

Requirements:

    Issue Summary (that is often what executives will read) must contain:
        duration of the outage with start and end times (including timezone)
        what was the impact (what service was down/slow? What were user experiencing? How many % of the users were affected?)
        what was the root cause

    Timeline (format bullet point, format: time - keep it short, 1 or 2 sentences) must contain:
        when was the issue detected
        how was the issue detected (monitoring alert, an engineer noticed something, a customer complained…)
        actions taken (what parts of the system were investigated, what were the assumption on the root cause of the issue)
        misleading investigation/debugging paths that were taken
        which team/individuals was the incident escalated to
        how the incident was resolved

    Root cause and resolution must contain:
        explain in detail what was causing the issue
        explain in detail how the issue was fixed

    Corrective and preventative measures must contain:
        what are the things that can be improved/fixed (broadly speaking)
        a list of tasks to address the issue (be very specific, like a TODO, example: patch Nginx server, add monitoring on server memory…)

    Be brief and straight to the point, between 400 to 600 words

While postmortem format can vary, stick to this one so that you can get properly reviewed by your peers.

Please, remember that these blogs must be written in English to further your technical ability in a variety of settings.
Add URLs here:

    https://docs.google.com/document/d/1U0iUIbU6U3ovcK0KDu8-xRv8ik-8kCWos8w-NM0vDl4/edit?usp=sharing 

Repo:

    GitHub repository: alx-system_engineering-devops
    Directory: 0x19-postmortem
    File: README.md

1. Make people want to read your postmortem
#advanced
Score: 100.0% (Checks completed: 100.0%)

We are constantly stormed by a quantity of information, it’s tough to get people to read you.

Make your post-mortem attractive by adding humour, a pretty diagram or anything that would catch your audience attention.

Please, remember that these blogs must be written in English to further your technical ability in a variety of settings.
Add URLs here:

    https://docs.google.com/document/d/1LbNXe0iu_QA6gfZoyuuyalHmsfwE2YSIO0E8OMk7aAw/edit?usp=sharing 

Repo:

    GitHub repository: alx-system_engineering-devops
    Directory: 0x19-postmortem
    File: README.md

Copyright © 2023 ALX, All rights reserved.








Issue Summary:
Duration: August 5, 2023, 02:00 AM - 04:30 AM (UTC)
Impact: Database Service Outage - Users experienced intermittent connectivity issues and slow response times. Approximately 30% of users were affected.
Root Cause: Sudden spike in incoming database connections triggered resource exhaustion.

Timeline:
- 02:00 AM: Monitoring system flagged increased latency on database queries.
- 02:15 AM: Incident acknowledged by on-call engineer due to user complaints about slow application performance.
- 02:30 AM: Initial investigation indicated potential networking issue.
- 02:45 AM: Networking team found no abnormalities, attention shifted to database systems.
- 03:00 AM: Assumption made that recent code deployment might be causing excessive queries.
- 03:15 AM: Query optimizations performed to mitigate, no significant improvement.
- 03:30 AM: Escalation to database team as issue persisted; suspected a query locking scenario.
- 04:00 AM: After in-depth analysis, query locking theory disproven.
- 04:15 AM: Engaged senior database engineer who identified a sudden spike in incoming connections.
- 04:30 AM: Identified connection pooling exhaustion as root cause and applied a temporary fix.



Root Cause and Resolution:
Root Cause: Connection pool exhaustion due to an unexpectedly high number of incoming connections.
Resolution: Increased connection pool limits, tuned timeouts, and implemented stricter connection monitoring.

Corrective and Preventative Measures:
- Improve monitoring: Implement real-time connection tracking and alerts for unusual spikes.
- Load testing: Conduct stress testing to determine connection pool capacity.
- Auto-scaling: Implement automated scaling of database resources during traffic spikes.
- Code review: Enhance query efficiency and connection management in application code.
- Documentation: Update incident response protocols to include connection pool issues.

This incident demonstrated the critical importance of monitoring database connections proactively. By accurately detecting and responding to connection pool exhaustion, we can prevent service disruptions and ensure a seamless user experience. Our immediate measures helped restore service, but we acknowledge the need for more robust preventive strategies.

In the future, we plan to enhance our system's scalability by automating the provisioning of additional database resources based on traffic patterns. Additionally, we will collaborate closely with the development team to optimize code and minimize unnecessary database interactions. A comprehensive review of our monitoring systems will be conducted, ensuring timely alerts for any anomalies.

To address this incident, we've outlined the following tasks:
1. Implement automated connection pool scaling based on demand.
2. Update monitoring thresholds and alerts for connection pool usage.
3. Review and optimize application code to minimize database interactions.
4. Conduct regular load testing to assess system capacity and performance.
5. Develop documentation detailing incident response procedures for connection pool issues.

Through these corrective measures and preventive actions, we aim to strengthen our infrastructure's resilience, minimize downtime, and uphold the high standard of service our users expect. We appreciate the diligence of our teams during this incident and remain committed to delivering a seamless user experience.

