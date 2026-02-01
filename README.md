# DoorDash Meal Reminder Bot

Sends a Slack notification every Saturday and Sunday morning at 9am PT with a link to the team's DoorDash meal calendar.

## Testing

To test immediately without waiting for the schedule:

1. Go to **Actions** tab in your repo
2. Select **DoorDash Meal Reminder**
3. Click **Run workflow** → **Run workflow**

### Customization

### Change the schedule

Edit `.github/workflows/notify.yml` and modify the cron expression:

```yaml
schedule:
  - cron: '0 16 * * 0,6'  # 9am PT on Sat (6) and Sun (0)
```

Cron format: `minute hour day month weekday` (UTC timezone)

### Change the message

Edit the `text` field in the workflow file. Slack link format: `<URL|display text>`


......



## How to set up for future workspaces

### 1. Get Doordash for Business Link

1. Login to [Doordash for Business](https://www.doordash.com/teams/admin)
2. Click **Group Orders**
3. Click **Share Meal Calendar** and copy url.
4. Go to your GitHub repo → Settings → Secrets and variables → Actions
5. Click the Variables tab
6. Click New repository variable
7. Name: DOORDASH_CALENDAR_URL

### 2. Create a Slack Incoming Webhook

1. Go to [Slack App Management](https://api.slack.com/apps)
2. Click **Create New App** → **From scratch**
3. Name it something like "Meal Reminder" and select your workspace
4. Go to **Incoming Webhooks** → Toggle **Activate Incoming Webhooks** to On
5. Click **Add New Webhook to Workspace**
6. Select the **#foods** channel and click **Allow**
7. Copy the Webhook URL (looks like `https://hooks.slack.com/services/T.../B.../xxx`)

### 3. Add the Webhook to GitHub Secrets

1. Go to your GitHub repo → **Settings** → **Secrets and variables** → **Actions**
2. Click **New repository secret**
3. Name: `SLACK_WEBHOOK_URL`
4. Value: Paste your webhook URL
5. Click **Add secret**

