# Zapier Template: Stalled Users → Email Alert

## Overview
This Zap identifies users who started onboarding but haven't reached first value after 24 hours, then sends an email alert for follow-up.

## Step-by-Step Setup

### Step 1: Create New Zap
1. Go to [zapier.com](https://zapier.com) and sign in
2. Click "Create Zap"
3. Name it: "Stalled Users → Email Alert"

### Step 2: Choose Trigger
1. Search for "PostHog" in the trigger apps
2. Select "PostHog"
3. Choose trigger event: "New Event"
4. Connect your PostHog account:
   - API Key: `phc_3ACn7GrUe4Qzji0iXMvm7dmyL3XDx7G36SfUH9TQ4il`
   - Host: `https://us.i.posthog.com`
5. Configure trigger:
   - Event name: `onboarding_started`
   - Time range: "Last 24 hours"

### Step 3: Add Delay
1. Click "Add step" → "Delay"
2. Choose "Delay by"
3. Set delay: 24 hours
4. This ensures we only alert after 24 hours have passed

### Step 4: Add Filter
1. Click "Add step" → "Filter"
2. Set up filter to check if user has NOT fired `first_value`:
   - Field: `event_name`
   - Condition: "does not contain"
   - Value: `first_value`
3. This prevents alerts for users who already reached first value

### Step 5: Add Action
1. Click "Add action"
2. Search for "Gmail" or "Email by Zapier"
3. Select your preferred email service
4. Choose action: "Send Email"

### Step 6: Configure Email Action
1. Connect your email account
2. Configure email:

**To:** `your-team@company.com` (or specific team member)
**Subject:** `🚨 User stalled after 24h - {{user_id}}`
**Body:**
```
Hi team,

A user has been stalled for 24+ hours after starting onboarding.

**User Details:**
- User ID: {{user_id}}
- Started onboarding: {{timestamp}}
- Source: {{source}}
- Plan: {{plan}}
- Onboarding step: {{step}}

**Action Required:**
- Check if user needs help
- Send follow-up email
- Review onboarding flow for this step

**Quick Actions:**
- View user in PostHog: [Link to user profile]
- Send manual email
- Add to CRM for follow-up

---
Triggered by Zapier at {{zap_triggered_at}}
```

**Fields to Map:**
- `user_id` → `{{user_id}}`
- `timestamp` → `{{timestamp}}`
- `source` → `{{source}}`
- `plan` → `{{plan}}`
- `step` → `{{step}}`
- `zap_triggered_at` → `{{zap_triggered_at}}`

### Step 7: Test Action
1. Click "Test action"
2. Check your email for the test message
3. Verify all fields are populated correctly

### Step 8: Publish
1. Click "Publish Zap"
2. Set it to "On" status

## Alternative: Slack Notification

If you prefer Slack over email, replace Step 5 with:

### Step 5: Add Slack Action
1. Click "Add action"
2. Search for "Slack"
3. Select "Slack"
4. Choose action: "Send Channel Message"

**Channel:** `#user-support` or `#activation-alerts`
**Message:**
```
🚨 User stalled after 24h

**User:** {{user_id}}
**Started:** {{timestamp}}
**Source:** {{source}}
**Step:** {{step}}

*Needs follow-up attention*
```

## Advanced Configuration

### Multiple Recipients
Set up different emails for different scenarios:
- `support@company.com` - for general support issues
- `sales@company.com` - for high-value prospects
- `founder@company.com` - for VIP users

### Conditional Logic
Add filters to only alert for certain conditions:
- Filter by `source` = "landing" (only from your landing page)
- Filter by `plan` = "pro" (only paid users)
- Filter by `step` = "payment" (only users stuck on payment)

### Escalation Rules
Create multiple Zaps for escalation:
1. **24h Zap** (this one) - First alert
2. **48h Zap** - Escalation to manager
3. **72h Zap** - Escalation to founder

## Troubleshooting

### No Events Found
1. Check PostHog API key is correct
2. Verify event name: `onboarding_started`
3. Ensure events are being fired
4. Check time range settings

### Delay Not Working
1. Verify delay is set to 24 hours
2. Check Zap timezone settings
3. Ensure Zap is published and active

### False Positives
1. Check filter logic is correct
2. Verify `first_value` events are being tracked
3. Test with `/seed.html` to ensure data consistency

### Email Delivery Issues
1. Check email service connection
2. Verify recipient email addresses
3. Check spam/junk folders
4. Test with a different email service

## Monitoring

### Check Zap Performance
- Go to Zapier dashboard
- Monitor success/failure rates
- Check execution times
- Review error logs

### Track Alert Volume
- Monitor how many stalled user alerts you get
- Track response times to alerts
- Measure conversion rate from alerts to first_value

### Optimize Thresholds
- Adjust delay time based on your product
- Fine-tune filter conditions
- Add more specific targeting

## Best Practices

### Response Time
- Set up auto-responders for immediate acknowledgment
- Establish SLA for manual follow-up (e.g., 2 hours)
- Track time from alert to resolution

### Personalization
- Include user's name if available
- Reference specific onboarding step
- Add personalized help resources

### Documentation
- Keep track of common stall points
- Document successful intervention strategies
- Share learnings with product team

## Next Steps

1. Set up the "First Value" Zap (see separate template)
2. Create a dashboard to track stalled user metrics
3. Develop intervention playbook for different stall scenarios
4. A/B test different follow-up approaches

---

*This Zap will help you proactively identify and help users who are struggling to find value in your product, improving your overall activation rate.*
