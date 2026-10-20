# Testing and Validation

I validated the workflow with fictional scenarios covering every priority band.

## Test Matrix

| Lead | Event size | Timeline | Requirements | Expected | Verified |
|---|---|---|---|---:|---|
| Avery Chen — Northstar Events | 500–1,999 | Within 3 months | Three capabilities | High, 7/8 | Yes |
| Jordan Lee — BrightPath Events | 100–499 | 4–6 months | Two capabilities | Medium, 4/8 | Yes |
| Casey Morgan — Summit Community Meetup | Under 100 | Date undecided | Not sure yet | Low, 0/8 | Yes |

For each test, I verified that HubSpot contained:

- The correct contact identity and Lead Status
- The expected priority and score
- Qualification reasoning matching the visible point breakdown
- A lead summary and customer needs
- Three discovery questions
- A personalized draft marked for human review
- An associated next-day email task
- No automatically sent outbound message

## Processing-Time Evidence

| Test | Form submitted | HubSpot displayed activity | Supported conclusion |
|---|---|---|---|
| Jordan Lee | 1:58:35 a.m. EDT | 1:58 a.m. EDT | Completed within the same displayed minute |
| Casey Morgan | 2:10:56 a.m. EDT | 2:11 a.m. EDT | Completed by the next displayed minute |

HubSpot displays these activity timestamps at minute precision. I therefore report the observed result as same-minute or next-displayed-minute processing and do not invent an exact seconds-based latency.

## Evidence Boundaries

- Results reflect prototype tests performed on October 20, 2026.
- Data is fictional and does not represent real prospects.
- Performance can vary with vendor availability, API latency, and plan limits.
- No revenue, conversion-rate, or labour-hour improvement is claimed.

