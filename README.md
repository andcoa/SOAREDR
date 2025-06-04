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

![image](https://github.com/user-attachments/assets/c8646535-8ae6-42ca-bd34-be6fca10309c)

LimaCharlie confirms the installation on the Windows 10 VM.

![image](https://github.com/user-attachments/assets/85beaebf-55dd-4201-9a35-9fb6fbdea66d)

Installed the LaZagne Project (password recovery tool) to generate telemetry by running it in Powershell.

![image](https://github.com/user-attachments/assets/2fb9485b-7250-45db-bffe-4e954218ff39)

![image](https://github.com/user-attachments/assets/9c29dde8-9a44-4523-a389-f031ba364690)

The telemetry is available in LimaCharlie.

![image](https://github.com/user-attachments/assets/a304f4de-9969-4986-ae23-de7b4ab42e7a)

![image](https://github.com/user-attachments/assets/dfaae889-45ad-4cf3-8724-1cccc3e92b03)

Creawted a new rule in LimaCharlie to detect the use of Lazagne as per the following parameters:

![image](https://github.com/user-attachments/assets/5bf1ee86-d55b-4919-9d33-1617fb677c8e)

![image](https://github.com/user-attachments/assets/efa357b3-2a60-43a1-9c55-6b0792346a9c)

The rule succesfully executed and confirmed the event above was captured.

![image](https://github.com/user-attachments/assets/655a1e39-9de1-4efc-b846-82fd6b537718)

After executing Lazagne again, two detections were captured by the rule.

![image](https://github.com/user-attachments/assets/4f975882-2296-4738-820c-3aa24d92cbaf)

Created a new Slack organization and a channel named "alerts".

![image](https://github.com/user-attachments/assets/84646f2d-27f5-4b0a-a95f-28c7d6c31e16)

Created a Tines account and added a Webhook, which was then used to create a LimaCharlie output configuration using the Webhook URL.

![image](https://github.com/user-attachments/assets/4c39e948-a89a-48b9-8ad1-59a4173292cc)

![image](https://github.com/user-attachments/assets/8308b9c7-1940-423b-b471-410083aa2a10)

![image](https://github.com/user-attachments/assets/41b162c9-6bb1-4a68-a240-af675c7e5dbd)

Connected Slack to Tines to send/receive messages.

![image](https://github.com/user-attachments/assets/a712f61c-ea1d-474a-922e-99ca535a2d12)

Used the ChannelD from Slack to connect it with the Tines template.

![image](https://github.com/user-attachments/assets/7d3c414d-63f3-4c1e-822f-3b135faabd4d)

Slack is now connected to Tines and can receive messages.

![image](https://github.com/user-attachments/assets/f1acd583-9517-4fb8-824e-2b49f6ab5632)

Set up the "Send Email" template and successfully sent an email from Tines.

![image](https://github.com/user-attachments/assets/156fdb9a-e089-465b-9174-723a378a6c09)

![image](https://github.com/user-attachments/assets/9f7046c5-5883-499d-a279-9424b87f3bbd)

Created a user prompt page to allow the admin to isolate machines if needed:

![image](https://github.com/user-attachments/assets/bcbf5574-ad8b-44b7-81a1-47c14d3d57f5)

Copied the body values from the LimaCharlie webhook data in Tines over to Slack -> Message:

![image](https://github.com/user-attachments/assets/fb7d3ef2-ed40-4fa5-80c7-23e485f9669a)

![image](https://github.com/user-attachments/assets/37e35e20-7b2f-4fbb-b9a1-8b830a93bfb2)

Slack successfully received the LimaCharlie alert from the Tines webhook:

![image](https://github.com/user-attachments/assets/9638c963-d5a5-4c3c-a830-e24cbe7330d2)

Completed the same process for Send Email action and successfully received an email with the alert:

![image](https://github.com/user-attachments/assets/3a462f12-1e40-4b98-9713-78afea09d6b2)

![image](https://github.com/user-attachments/assets/7a4ee4ee-1d27-440e-99cc-e6d1283c6368)

Completed the same process for the User Prompt action as well and it succesfully created an interactive page for the analyst receiving the alert:

![image](https://github.com/user-attachments/assets/215aad2b-1886-4525-a474-9c0a51e96480)

Added a Trigger in Tines to send a Slack message when the user selects "No" as an input. Slack successfully received the message.

![image](https://github.com/user-attachments/assets/dd017682-52f0-47ea-ae9c-bbcfc84bba17)

![image](https://github.com/user-attachments/assets/c20a7662-e8f8-474a-8406-70ab8b712bba)

Repeated the same process to add a Trigger when selecting "Yes" and a LimaCharlie action to isolate the machine based on the response.

![image](https://github.com/user-attachments/assets/8c764030-bc99-4739-b1f4-f91843eb4a1f)

Used the Organization API found in LimaCharlie to connect it to the new Tines action.

![image](https://github.com/user-attachments/assets/23700ed0-38df-4f8b-a6b9-746570e9a74b)

![image](https://github.com/user-attachments/assets/a6460366-62ad-43f7-9f27-6693f3a632cc)

When re-emiting the event in the User Prompt and triggering the "Yes" action, the machine was isolated in LimaCharlie.

![image](https://github.com/user-attachments/assets/a1e17005-b81c-4195-8030-a5f173f2a3fd)

The Windows 10 VM is unable to interact with outside services after being isolated.

![image](https://github.com/user-attachments/assets/e9a9e5b9-4067-4dd1-942f-df0810aa0f51)

Added two a LimaCharlie action to get the isolation status of the machine into Tines and Slack action to receive the status.

![image](https://github.com/user-attachments/assets/406970b4-bf81-437e-b1ff-14064693d572)

![image](https://github.com/user-attachments/assets/acf8277c-1ba7-4b52-b0ba-f0d7207c4633)

Received the Slack message confirming the Windows 10 VM was isolated and email with the details of the alert.

![image](https://github.com/user-attachments/assets/29e0e347-02c8-4186-af03-858a56c45988)

![image](https://github.com/user-attachments/assets/8ae5bdf8-6b3a-4f01-b64b-46502a24f568)

Final workflow:

![image](https://github.com/user-attachments/assets/1f4455a4-ecda-49c9-8089-8645a68d47c3)

![Your first story-storyboard](https://github.com/user-attachments/assets/e00dc75c-df16-42ef-8d64-4b8a10346c67)






