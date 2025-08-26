# Zapier Template: First Value → Slack Notification

## Overview
This Zap sends a Slack notification whenever a user reaches first value, helping your team celebrate wins and identify patterns.

## Step-by-Step Setup

### Step 1: Create New Zap
1. Go to [zapier.com](https://zapier.com) and sign in
2. Click "Create Zap"
3. Name it: "First Value → Slack Alert"

### Step 2: Choose Trigger
1. Search for "PostHog" in the trigger apps
2. Select "PostHog"
3. Choose trigger event: "New Event"
4. Connect your PostHog account:
   - API Key: `phc_3ACn7GrUe4Qzji0iXMvm7dmyL3XDx7G36SfUH9TQ4il`
   - Host: `https://us.i.posthog.com`
5. Configure trigger:
   - Event name: `first_value`
   - Time range: "Last 24 hours" (for testing)

### Step 3: Test Trigger
1. Click "Test trigger"
2. If no events found, go to your `/seed.html` page and fire a `first_value` event
3. Refresh the test until you see the event
4. Select the test event and continue

### Step 4: Add Action
1. Click "Add action"
2. Search for "Slack"
3. Select "Slack"
4. Choose action: "Send Channel Message"

### Step 5: Configure Slack Action
1. Connect your Slack workspace
2. Choose channel: `#activation-wins` (or create this channel)
3. Configure message:

**Message Text:**
```
🎉 New user reached first value!

**User ID:** {{user_id}}
**Value Type:** {{value_type}}
**Time from Signup:** {{time_from_signup}} minutes
**Source:** {{source}}
**Plan:** {{plan}}

*Triggered at {{timestamp}}*
```

**Fields to Map:**
- `user_id` → `{{user_id}}`
- `value_type` → `{{value_type}}`
- `time_from_signup` → `{{time_from_signup}}`
- `source` → `{{source}}`
- `plan` → `{{plan}}`
- `timestamp` → `{{timestamp}}`

### Step 6: Test Action
1. Click "Test action"
2. Check your Slack channel for the test message
3. Verify all fields are populated correctly

### Step 7: Publish
1. Click "Publish Zap"
2. Set it to "On" status

## Customization Options

### Add User Properties
If you want to include more user context, add these to the message:
```
**User Email:** {{user_email}}
**Company:** {{company}}
**Role:** {{role}}
```

### Conditional Notifications
Add a filter step to only notify for certain conditions:
- Filter by `time_from_signup` < 30 (quick wins)
- Filter by `value_type` = "demo" (exclude test events)
- Filter by `source` = "landing" (only from your landing page)

### Different Channels
Create multiple Zaps for different audiences:
- `#sales` - for sales team to follow up
- `#product` - for product team insights
- `#founders` - for leadership updates

## Troubleshooting

### No Events Found
1. Check PostHog API key is correct
2. Verify event name matches exactly: `first_value`
3. Ensure events are being fired in PostHog
4. Try increasing time range to "Last 7 days"

### Missing Fields
1. Check that events include all required properties
2. Verify property names match exactly
3. Test with the `/seed.html` page to ensure consistent data

### Slack Connection Issues
1. Re-authenticate Slack connection
2. Check channel permissions
3. Verify bot is added to the channel

## Monitoring

### Check Zap Status
- Go to Zapier dashboard
- Look for failed runs
- Check error messages

### Test Regularly
- Use `/seed.html` to fire test events
- Verify Slack messages are received
- Check field mapping is correct

## Next Steps

1. Set up the "Stalled Users" Zap (see separate template)
2. Create a dashboard in Slack to track activation metrics
3. Add team reactions/celebrations to the channel
4. Consider adding to CRM for sales follow-up

---

*This Zap will help your team stay informed about user activation wins and identify patterns in how users find value in your product.*
