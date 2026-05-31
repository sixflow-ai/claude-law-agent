# Connectors

## How tool references work

This plugin's skills reference tools by category using a `~~` placeholder, so the
same plugin works no matter which specific product a firm uses. For example,
`~~email` means whichever email service the firm connects — Gmail, Outlook, or
another provider with a connector.

## Connectors for this plugin

| Category  | Placeholder   | Common options                          |
| --------- | ------------- | --------------------------------------- |
| Email     | `~~email`     | Gmail, Outlook / Microsoft 365          |
| Calendar  | `~~calendar`  | Google Calendar, Outlook Calendar       |
| Documents | `~~documents` | Google Drive, OneDrive, Box (optional)  |

`~~documents` is optional — document review also works on files the firm uploa