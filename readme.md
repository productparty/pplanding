# pplanding - Activation Landing Page

A tiny static site for tracking user activation with PostHog analytics. Deployed on Vercel.

## What this is

A simple landing page that helps founders track user activation metrics. Features:
- PostHog event tracking with UTM capture
- Embedded dashboard for real-time insights
- Links to Notion templates and Zapier automations
- Startup perks page with affiliate links
- Demo event seeding for testing

## Quick Start

### Run Locally
```bash
# Python 3
python -m http.server 3000

# Or Python 2
python -m SimpleHTTPServer 3000

# Then visit http://localhost:3000
```

### Deploy to Vercel
1. Push to GitHub
2. Connect repo to Vercel
3. Deploy automatically on push

## Configuration

### PostHog Setup
1. Get your Project API key from PostHog
2. Update the key in `index.html` and `seed.html`:
   ```javascript
   posthog.init('YOUR_API_KEY', {
     api_host: 'https://us.i.posthog.com'
   });
   ```

### Dashboard Embed
1. In PostHog, go to your Activation dashboard
2. Click "Share" → "Public link"
3. Copy the URL and replace `POSTHOG_PUBLIC_DASHBOARD_URL` in `index.html`

### Checkout URL
Replace `CHECKOUT_URL` in `index.html` with your actual checkout link:
```html
<a id="cta" href="https://your-checkout.com" class="button">Get Starter Pack</a>
```

### Notion & Zapier Links
Update the placeholder links in the Resources section:
```html
<a href="https://your-notion-template.com" class="button">Duplicate Notion template</a>
<a href="https://your-zap-templates.com" class="button">Turn on Zap templates</a>
```

## File Structure
```
/
├── index.html          # Main landing page
├── perks.html          # Startup discounts page
├── seed.html           # Demo event generator
├── README.md           # This file
└── notion_playbook_lite.md  # Notion template content
```

## Events Tracked

- `sign_up` - User clicks CTA
- `onboarding_started` - User begins onboarding
- `onboarding_completed` - User finishes onboarding
- `first_value` - User gets first value from product
- `habit_action` - User performs habitual action

## Customization

### Adding New Perks
Edit `perks.html` to add more startup programs:
```html
<li><strong>New Tool</strong> — Description. <a href="#">Apply</a></li>
```

### Modifying Events
Update event properties in the JavaScript sections of each file to match your tracking needs.

### Styling
All styles are inline CSS. Modify the `<style>` sections to change appearance.

## PostHog Cohorts to Create

1. **Activated Users**: Users who fired `first_value` within 7 days of `sign_up`
2. **Stalled Users**: Users who fired `onboarding_started` but no `first_value` after 24 hours

## PostHog Alert to Set

**Low Activation Rate**: Alert when activation rate (first_value/sign_up) drops below 15% in a 24-hour period.

## Next Steps

1. Replace placeholder URLs with real links
2. Create PostHog cohorts and alerts
3. Set up Zapier automations
4. Add success page for post-checkout tracking
5. Integrate with your actual product onboarding flow

## Support

For issues or questions, check the PostHog documentation or create an issue in this repo.
