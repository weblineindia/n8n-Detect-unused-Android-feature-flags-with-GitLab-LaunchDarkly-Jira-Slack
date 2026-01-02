# Detect unused Android feature flags with GitLab, LaunchDarkly, Jira & Slack

This n8n automation detects unused (“dead”) feature flags in an Android Kotlin/Java codebase by comparing your GitLab repository code against LaunchDarkly’s feature flag list. It logs results in Google Sheets, creates Jira cleanup tickets, and sends Slack alerts automatically. :contentReference[oaicite:1]{index=1}

---

## Who’s It For

- Android engineering teams using Kotlin/Java.
- Teams managing feature flags in LaunchDarkly.
- DevOps/QA teams wanting to reduce technical debt from stale flags. :contentReference[oaicite:2]{index=2}

---

## How It Works

1. **Weekly Trigger** runs the process.
2. **GitLab Node** fetches repository code.
3. **Regex Extraction** finds all feature flags in code.
4. **LaunchDarkly API** retrieves all configured flags.
5. **Comparison Logic** marks flags as “dead” if unused in code and archived or off in production.
6. **Google Sheets** stores flagged results.
7. **Jira** creates a ticket for each dead flag.
8. **Slack** notifies the team. :contentReference[oaicite:3]{index=3}

---

## How to Set Up

1. Import the workflow JSON into your n8n instance.
2. Connect credentials for:
   - GitLab OAuth2
   - Google Sheets
   - Jira
   - Slack webhook URL
3. Update:
   - GitLab repo details in the GitLab node.
   - LaunchDarkly API key in the HTTP Request node.
   - Google Sheet ID in the Google Sheets node.
   - Jira project & issue type in the Jira node.
   - Slack message formatting in the Slack node.
4. Activate the workflow. :contentReference[oaicite:4]{index=4}

---

## Requirements

- n8n (self-hosted or cloud)
- GitLab repository with Kotlin/Java code
- LaunchDarkly account with API token
- Google Sheets API access
- Jira API access
- Slack incoming webhook :contentReference[oaicite:5]{index=5}

---

## How to Customize

- Change regex pattern in the “Detect flags” node to match your feature flag naming convention.
- Adjust dead flag logic (e.g., treat test or staging flags differently).
- Modify Slack message content to include more details like the flag description from LaunchDarkly.
- Add email notifications for broader distribution using Gmail or SMTP nodes. :contentReference[oaicite:6]{index=6}

---

## Add-Ons

- **Email Alerts** via Gmail/SMTP for additional notifications.
- **GitLab Merge Requests** to remove dead flags automatically.
- **Confluence Integration** to document flag cleanup history. :contentReference[oaicite:7]{index=7}

---

## Use Case Examples

- Weekly automated cleanup alerts for large engineering teams.
- Maintain a clean feature flag list in high-traffic apps.
- Compliance-driven projects requiring feature flag lifecycle tracking. :contentReference[oaicite:8]{index=8}

---

## Common Troubleshooting

| Issue                                | Possible Cause                                | Solution                                                 |
| ------------------------------------ | --------------------------------------------- | -------------------------------------------------------- | ------------------------------------- |
| Workflow fails at GitLab node        | Invalid repo path or missing OAuth scope      | Update repo path & check GitLab OAuth permissions        |
| LaunchDarkly API request returns 401 | Invalid or expired API key                    | Generate a new API key in LaunchDarkly & update node     |
| Google Sheets node fails             | Wrong Sheet ID or missing sharing permissions | Confirm Sheet ID and share with connected Google account |
| Jira ticket not created              | Missing required fields                       | Set project key, issue type, and summary in Jira node    |
| Slack alert not sent                 | Webhook URL invalid or revoked                | Regenerate Slack webhook and update in node              | :contentReference[oaicite:9]{index=9} |

---

## Need Help?

If you’d like help setting up and customizing this workflow for your exact repo, flag rules, and team notification preferences — including regex adjustments, extra reporting, or adding automatic cleanup PRs — our n8n automation team at **WeblineIndia** is happy to assist! :contentReference[oaicite:10]{index=10}
