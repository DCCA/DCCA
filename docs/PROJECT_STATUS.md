# Project status

Session log for the DCCA profile (GitHub profile README, LinkedIn alignment, traffic attribution). Newest first.

## 2026-08-23 - Profile review, GitHub/LinkedIn alignment, UTM tracking

**Where we were:** GitHub profile had three different taglines (bio, README, repo description), 2 pinned repos vs 5 listed in the README, empty website/company fields, 13 undescribed tutorial repos, and no way to attribute aisignaldesk.ai traffic to either profile. LinkedIn About was two lines; last four roles had no descriptions.

**What we did:**
- README: shared headline, UTM-tagged AI Signal Desk links, Background adds PSafe and the BI origin, self-referencing GitHub link removed (#1, merged, `6bbadf0`).
- README anti-slop pass: em dashes 8 -> 0, decorative triplets and contrast pairs rewritten (#2, open).
- GitHub profile fields set via API: bio = shared headline, company = Neon, website = `https://aisignaldesk.ai` (clean URL; attribution for bio clicks comes from the github.com referrer instead).
- `dcca-sk` repo got a description.
- PostHog (project "AI Signal Desk"): saved insight "Profile referrals: GitHub vs LinkedIn" (short id `pFkQBOaH`) counting pageviews with `utm_medium=profile` or referrer `github.com`, broken down by `coalesce(utm_source, $referring_domain)`. Verified it runs and already shows the two historical github.com visits.
- LinkedIn reviewed from screenshots: 7 errors found (Mercado Libre/Neon date overlap, "Bussiness", "18 a 20 [milhões]", "webmotos", "Intellignece" x2, "perfomance", Gauge sub-role overlap). Four About drafts written and rejected; a 5-reviewer adversarial pass ran on the third.

**Decisions:**
- UTM scheme for any profile link to aisignaldesk.ai: `utm_source=github|linkedin`, `utm_medium=profile`, `utm_campaign=readme|about|featured|contact`.
- GitHub sidebar website stays a clean URL because GitHub renders the raw query string; bio clicks are attributed by referrer.
- LinkedIn About: paused. Owner's criteria after four drafts: audience is founders and potential partners (not recruiters), text must be in the owner's own voice, short, without project/GitHub numbers, and with a different positioning than "PM who codes". Blocked on a voice sample, the angle in the owner's words, and the desired call to action.
- GitHub pinning cannot be done via API (no GraphQL mutation); profile PATCH needed the `user` OAuth scope, granted this session.

**Pending / next:**
- [ ] Merge or close #2 (anti-slop README).
- [ ] Pin 6 repos manually: skval, vyno, shotback, loopy, sandy, firehose.
- [ ] Decide on the 13 public tutorial repos (private or archive): word-press-camping, todoapp, buildspace-dao-starter, kickstart, lottery-react, lottery, inbox-updated, inbox, ubuntu-help, InstaNews-1, alohap1, color-game, FlashLigh-Banban.
- [ ] LinkedIn: fix the 7 errors, set headline to the shared one, add Featured links with `utm_campaign=featured`, write the four empty role descriptions (needs area, team size, one outcome each).
- [ ] LinkedIn About: resume only with the owner's voice sample, angle, and call to action. Then re-run the adversarial panel with the criterion "would a founder in São Paulo message him".
- [ ] Optional: `/gh` redirect on aisignaldesk.ai that appends UTMs, so the sidebar can carry attribution with a clean URL.
