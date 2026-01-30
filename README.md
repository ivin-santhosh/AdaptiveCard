# IT Helpdesk : Adaptive Cards Research & Implementation

This repository contains research and JSON schema samples for implementing **Adaptive Cards** within the AstraFin IT Helpdesk Agent (Microsoft Copilot Studio). 

## 1. Why Adaptive Cards?
In an IT Support context, "text bubbles" often lead to user friction. We use Adaptive Cards for the following reasons:

* **Data Validation:** Unlike open text fields, Adaptive Cards use dropdowns, radio buttons, and date pickers. This ensures the data sent to Power Automate is in the correct format (e.g., a "Date" is actually a date, not "yesterday").
* **Reduced User Error:** By providing specific buttons (e.g., Windows, Mac, Linux), we eliminate typos that would otherwise cause a "Topic" to fail or a "Flow" to crash.
* **Structured Feedback:** They allow for a "Submit" action, which bundles multiple user inputs into a single JSON object, reducing the number of back-and-forth turns in a conversation.

---

## 2. Adaptive Card JSON Samples

### Example A: OS Selection (Input ChoiceSet)
Used for determining a user's operating system with 100% accuracy.

```json
{
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "TextBlock",
            "size": "Medium",
            "weight": "Bolder",
            "text": "System Configuration"
        },
        {
            "type": "TextBlock",
            "text": "Which Operating System are you currently using?",
            "wrap": true
        },
        {
            "type": "Input.ChoiceSet",
            "id": "OSSelection",
            "style": "expanded",
            "choices": [
                { "title": "Windows 11", "value": "Win11" },
                { "title": "macOS (Sequoia/Sonoma)", "value": "macOS" },
                { "title": "Linux (Ubuntu/Debian)", "value": "Linux" }
            ]
        }
    ],
    "actions": [
        {
            "type": "Action.Submit",
            "title": "Submit Selection"
        }
    ],
    "$schema": "[http://adaptivecards.io/schemas/adaptive-card.json](http://adaptivecards.io/schemas/adaptive-card.json)",
    "version": "1.3"
}
```
### Example B: Hardware Request Form
Used for the "Request a New Laptop" scenario to gather multiple data points at once.

```json
{
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hardware Request Form",
            "weight": "Bolder",
            "size": "Large"
        },
        {
            "type": "Input.Text",
            "id": "AssetReason",
            "placeholder": "Reason for request (e.g. New Hire, Damaged)",
            "isMultiline": true
        },
        {
            "type": "Input.Date",
            "id": "RequiredDate",
            "title": "Required By Date"
        }
    ],
    "actions": [
        {
            "type": "Action.Submit",
            "title": "Submit Request"
        }
    ],
    "$schema": "[http://adaptivecards.io/schemas/adaptive-card.json](http://adaptivecards.io/schemas/adaptive-card.json)",
    "version": "1.3"
}
```

## 3. Reference Documentation
- <b>Adaptive Cards Schema Explorer</b>  -> [Here](https://adaptivecards.io/explorer/)
- <b>Microsoft Copilot Studio: Use Adaptive Cards</b> -> [Here](https://www.google.com/search?q=https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-adaptive-cards)
