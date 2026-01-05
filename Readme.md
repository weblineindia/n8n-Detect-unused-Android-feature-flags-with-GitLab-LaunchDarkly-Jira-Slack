
# Detect Unused Android Feature Flags with GitLab, LaunchDarkly, Jira & Slack

This n8n automation detects unused (“dead”) feature flags in an Android Kotlin/Java codebase by comparing feature flag usage in your GitLab repository against the list of flags configured in LaunchDarkly.
The workflow logs results in Google Sheets, creates Jira cleanup tickets, and sends Slack alerts automatically to reduce technical debt.

---

## Who’s It For

* Android engineering teams using Kotlin or Java
* Teams managing feature flags with LaunchDarkly
* DevOps and QA teams aiming to reduce stale feature flags and technical debt

---

## How It Works

1. **Weekly Schedule Trigger** starts the workflow.
2. **GitLab Node** fetches repository files.
3. **Regex Extraction** scans the codebase to detect feature flag references.
4. **LaunchDarkly API** retrieves all existing feature flags.
5. **Comparison Logic** identifies “dead” flags that are:

   * Not referenced in code, and
   * Archived or disabled in production
6. **Google Sheets** logs all detected unused flags.
7. **Jira** creates cleanup tickets for each dead flag.
8. **Slack** sends a summary notification to the team.

---

## How to Set Up

1. Import the workflow JSON into your n8n instance.
2. Configure credentials for:

   * GitLab (OAuth2 or personal access token)
   * Google Sheets
   * Jira
   * Slack (Incoming Webhook or Bot token)
3. Update the following nodes:

   * **GitLab Node** – repository URL, branch, and file paths
   * **HTTP Request Node** – LaunchDarkly API key
   * **Google Sheets Node** – spreadsheet ID and target sheet
   * **Jira Node** – project key, issue type, and required fields
   * **Slack Node** – channel and message format
4. Activate the workflow.

---

## Requirements

* n8n (cloud or self-hosted)
* GitLab repository with Android Kotlin/Java code
* LaunchDarkly account with an API token
* Google Sheets API access
* Jira API access
* Slack workspace with webhook or bot permissions

---

## How to Customize

* Update the regex pattern to match your feature flag naming convention
* Change the dead-flag criteria (e.g., treat staging-only flags differently)
* Enrich Slack messages with flag metadata from LaunchDarkly
* Add email notifications using Gmail or SMTP nodes
* Adjust the schedule (daily, bi-weekly, or on-demand)

---

## Add-Ons

* **Email Alerts** – Notify stakeholders via Gmail or SMTP
* **Automatic Cleanup PRs** – Create GitLab merge requests to remove dead flags
* **Confluence Integration** – Maintain documentation for feature flag lifecycle and cleanup history

---

## Use Case Examples

* Weekly automated reports highlighting unused feature flags
* Maintaining a clean and manageable flag list in large Android apps
* Supporting compliance or audit requirements around feature flag usage

---

## Common Troubleshooting

| Issue                        | Possible Cause                           | Solution                                                 |
| ---------------------------- | ---------------------------------------- | -------------------------------------------------------- |
| GitLab node fails            | Invalid repo path or missing permissions | Verify repository path and OAuth scopes                  |
| LaunchDarkly API returns 401 | Invalid or expired API key               | Generate a new API key and update the workflow           |
| Google Sheets write fails    | Incorrect Sheet ID or permissions        | Confirm Sheet ID and share it with the connected account |
| Jira issue not created       | Missing required fields                  | Set project key, issue type, and summary correctly       |
| Slack alert not sent         | Invalid or revoked webhook URL           | Regenerate and update the Slack webhook                  |

---

## Need Help?

If you’d like help configuring or extending this workflow—such as refining regex detection, adding detailed reporting, or enabling automatic cleanup merge requests—our **n8n automation experts at WeblineIndia** are happy to assist.
