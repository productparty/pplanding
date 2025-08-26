# Activation Playbook (Lite)

*Copy this entire document into a new Notion page to track your user activation metrics and experiments.*

---

## 🎯 KPI Tree

### Primary Goal
**Increase % of users who reach first value within 7 days**

### Key Metrics
- **Activation Rate**: first_value / sign_up (target: 15%+)
- **Time to First Value**: Average minutes from sign_up to first_value (target: < 30 min)
- **Onboarding Completion**: onboarding_completed / onboarding_started (target: 80%+)

### Leading Indicators
- Onboarding step completion rates
- Feature usage in first session
- Support ticket volume
- Email open/click rates

---

## 📊 Event Schema

| Event | Key Properties | When to Fire |
|-------|---------------|--------------|
| `sign_up` | source, plan, utm_* | User clicks CTA or completes registration |
| `onboarding_started` | step, utm_* | User begins any onboarding flow |
| `onboarding_completed` | time_to_complete, steps_completed | User finishes all required onboarding |
| `first_value` | value_type, time_from_signup, feature_used | User gets meaningful value from product |
| `habit_action` | count_7d, count_28d, action_type | User performs core product action |

### Property Definitions
- **source**: Where user came from (landing, referral, organic)
- **plan**: User's subscription tier (free, pro, enterprise)
- **value_type**: Type of value received (demo, feature, insight, connection)
- **time_from_signup**: Minutes elapsed since sign_up event
- **count_7d**: Number of actions in last 7 days

---

## 🧪 12 Zero-Budget Experiments

### Week 1-2: Onboarding Optimization
1. **Welcome Email Sequence**
   - Goal: Increase onboarding completion rate
   - Setup: 3-email sequence over 7 days
   - Metric: onboarding_completed rate
   - Stop rule: No improvement after 2 weeks

2. **Progressive Disclosure**
   - Goal: Reduce cognitive load during onboarding
   - Setup: Show only 1-2 fields per step
   - Metric: Time to onboarding_completed
   - Stop rule: If completion rate drops

3. **Social Proof Integration**
   - Goal: Build trust during signup
   - Setup: Add customer testimonials to key steps
   - Metric: sign_up to onboarding_started conversion
   - Stop rule: No significant improvement

### Week 3-4: Value Delivery
4. **Quick Win Feature**
   - Goal: Get users to first_value faster
   - Setup: Highlight easiest-to-use feature first
   - Metric: Time to first_value
   - Stop rule: If activation rate doesn't improve

5. **Personalized Onboarding**
   - Goal: Match onboarding to user intent
   - Setup: Ask 1 question during signup, customize flow
   - Metric: first_value rate by user type
   - Stop rule: If complexity increases drop-off

6. **Feature Tour**
   - Goal: Educate users on key features
   - Setup: Interactive walkthrough of 3 main features
   - Metric: Feature usage in first session
   - Stop rule: If session duration decreases

### Week 5-6: Engagement & Retention
7. **Habit Formation**
   - Goal: Increase habit_action frequency
   - Setup: Daily/weekly reminder emails
   - Metric: habit_action count_7d
   - Stop rule: If unsubscribe rate spikes

8. **Community Integration**
   - Goal: Increase user engagement
   - Setup: Add community features or links
   - Metric: Time spent in product
   - Stop rule: If core metrics decline

9. **Gamification Elements**
   - Goal: Increase user motivation
   - Setup: Progress bars, achievements, streaks
   - Metric: Session frequency
   - Stop rule: If perceived as gimmicky

### Week 7-8: Optimization
10. **A/B Test CTA Copy**
    - Goal: Improve sign_up conversion
    - Setup: Test 3 different CTA variations
    - Metric: sign_up rate
    - Stop rule: After statistical significance

11. **Landing Page Optimization**
    - Goal: Improve traffic quality
    - Setup: Test different value propositions
    - Metric: sign_up to first_value rate
    - Stop rule: If conversion rate drops

12. **Email Timing Optimization**
    - Goal: Improve email engagement
    - Setup: Test different send times
    - Metric: Email open/click rates
    - Stop rule: After 2 weeks of testing

---

## 📅 Weekly Review Checklist

### Data Review (Monday)
- [ ] Check activation rate for past week
- [ ] Review time to first_value trends
- [ ] Analyze onboarding drop-off points
- [ ] Check for any data anomalies

### Experiment Status (Tuesday)
- [ ] Review active experiments
- [ ] Check if any experiments hit stop rules
- [ ] Plan next week's experiments
- [ ] Document learnings from completed experiments

### User Feedback (Wednesday)
- [ ] Review support tickets related to onboarding
- [ ] Check user interviews/surveys
- [ ] Analyze feature request patterns
- [ ] Look for common pain points

### Optimization (Thursday)
- [ ] Identify quick wins from data
- [ ] Plan A/B tests for next week
- [ ] Update onboarding flows if needed
- [ ] Review and update event tracking

### Team Sync (Friday)
- [ ] Share weekly metrics with team
- [ ] Discuss experiment results
- [ ] Plan next week's priorities
- [ ] Celebrate wins and learnings

---

## 🚨 Alerts & Monitoring

### Daily Checks
- Activation rate below 10%
- Time to first_value above 60 minutes
- Onboarding completion rate below 70%

### Weekly Reviews
- Compare metrics to previous week
- Review experiment performance
- Check for seasonal patterns

### Monthly Deep Dives
- Full funnel analysis
- Cohort retention analysis
- Feature usage patterns
- User journey mapping

---

## 📈 Success Metrics

### Month 1 Targets
- Activation rate: 10% → 15%
- Time to first value: 45 min → 30 min
- Onboarding completion: 70% → 80%

### Month 2 Targets
- Activation rate: 15% → 20%
- Time to first value: 30 min → 20 min
- Onboarding completion: 80% → 85%

### Month 3 Targets
- Activation rate: 20% → 25%
- Time to first value: 20 min → 15 min
- Onboarding completion: 85% → 90%

---

*Remember: Start small, measure everything, and iterate based on data. This playbook is a living document - update it as you learn what works for your specific users and product.*
