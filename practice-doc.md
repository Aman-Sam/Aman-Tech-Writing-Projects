title: Notification bot.
author: amanprasad

description: Learn how a notification bot works in Teams, and to customize notification behavior.
ms.localizationpriority: high

# Notification bot in Teams

Microsoft Teams Toolkit enables you to build applications that capture events and send them as notifications to a personal, group chat, or a channel in Teams. You can send notifications as plain text or Adaptive Cards. The notification bot template creates an app that sends a message to Teams with Adaptive Cards triggered by HTTP post request.

The app template is built using the TeamsFx SDK, which provides a simple set of functions over Microsoft Bot Framework to implement your requirement. For example, in a scenario where a travel agency builds an app in Teams for their customers to keep them up-to-date with the weather forecast. In the following diagram you can see a Teams app that sends notification to the travelers about the destination weather forecast:

[Placeholder for an image]

You can create notification bot in other scenarios, such as a notification can be sent in teams DevOps channel if there's a build failure.

**Advantages**

- Facilitates notifications to a personal, group chat, and in a channel, using APIs from TeamsFx SDK.
- Enhances user experience by customizing notification with an Adaptive Card.
- Provides multiple mechanisms to trigger notifications such as HTTP and schedule timer trigger with Azure Functions.


> [!NOTE]
> Bot application needs to be installed with the corresponding scope before sending notification.

## Notification based on events

Bot Framework SDK provides the functionality to proactively message in Teams. TeamsFx SDK provides the functionality to manage bot's conversation references when a bot event is triggered. TeamsFx SDK recognizes the following bot events:


|Event  |Behavior  |
|---------|---------|
The first time you install a bot to a person, group, or Team.   |Add the target conversation reference to the storage.         |
|When the bot is uninstalled from a person, group, or Team.     |Remove the target conversation reference from the storage.         |
When the team installed by bot is deleted.   |Remove the target conversation reference from the storage.         |
|When the team installed by bot is restored.     |Add the target conversation reference to the storage.         |
|When the bot sends messages.     |When the target conversation reference doesn't exist, add it to the storage.         |

[Placeholder for an image]

When you send notifications, TeamsFx SDK creates a new conversation from the selected conversation reference, and then sends a message. For advanced usage, you can directly access the conversation reference to execute your own bot logic: