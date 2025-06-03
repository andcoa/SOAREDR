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

- **Vultr**: Cloud servoce for hosting the Windows 10 Server VM.
- **LimaCharlie**: Cloud-native EDR for event detection.
- **Tines**: SOAR platform for playbook orchestration.
- **Slack & Email**: Channels for alert notification.
- **Virtualbox**: Hosting Virtual Machines.
- **JSON**: Export format for playbook definitions.

## Steps

Designed the architecture of the SOAR EDR using draw.io.

![image](https://github.com/user-attachments/assets/b4b38889-980b-483a-9caf-0498a3fa86f0)

Deployed a Windows 10 Server VM in Vultr using the lowest plan available (to keep costs within the free trial).

![image](https://github.com/user-attachments/assets/414ea4ab-d081-407a-a9ae-843fa811986a)

Created a Firewall group to be able to remotely connect to the VM.

![image](https://github.com/user-attachments/assets/f01d3c7c-70a2-48dd-920c-8be16e5cfb03)



Signed up for LimaCharlie and created the following organization:

![image](https://github.com/user-attachments/assets/e4a648f3-92d4-49e1-b822-460f078d0adb)

Created an installation key.

![image](https://github.com/user-attachments/assets/9798b2aa-b4c7-4670-b50d-f26d5bc50278)

Downloaded and installed the LimaCharlie sensor on the Windows 10 VM.

![image](https://github.com/user-attachments/assets/e2aca47e-7c15-4ddd-a3fd-e181f7c0f08b)


