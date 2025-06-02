# SOAR EDR Project


## Objective
Design and implement a modular SOAR-EDR playbook workflow that detects suspicious activity via LimaCharlie, escalates alerts through Tines, notifies via Slack and email, and provides an interactive decision point for automated endpoint isolation.

## Skills Learned

- **Playbook Design**: Mapped out end-to-end SOAR logic, detection, escalation, notification, and containment in a clear workflow.
- **EDR Integration**: Configured LimaCharlie to detect a “hack tool” event and forward alerts programmatically.
- **SOAR Orchestration**: Utilized Tines to receive detections, branch logic, and invoke downstream actions.
- **Notification Engineering**: Structured Slack and email messages to include key telemetry (timestamp, hostname, source IP, process command line, file path, sensor ID, detection link).
- **Interactive Containment**: Built a user prompt node to conditionally isolate the machine and report status back to Slack.

## Tools Used

- **Vultr**: Cloud servoce for hosting the Windows 10 VM.
- **LimaCharlie**: Cloud-native EDR for event detection.
- **Tines**: SOAR platform for playbook orchestration.
- **Slack & Email**: Channels for alert notification.
- **Virtualbox**: Hosting Virtual Machines.
- **JSON**: Export format for playbook definitions.

## Steps

Designed the architecture of the SOAR EDR using draw.io.

![image](https://github.com/user-attachments/assets/b4b38889-980b-483a-9caf-0498a3fa86f0)

