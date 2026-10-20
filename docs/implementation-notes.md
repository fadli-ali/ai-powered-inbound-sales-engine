# Implementation Notes

## Scenario Components

1. Tally — Watch New Responses
2. Make Tools — Set Variables / preserve submission time
3. OpenAI — Generate structured sales analysis
4. JSON — Parse and validate the response fields
5. HubSpot — Create or update contact
6. HubSpot — Create associated note
7. HubSpot — Create associated follow-up task

## Structured AI Output

The workflow expects these fields:

- `priority`
- `score`
- `score_breakdown`
- `qualification_reason`
- `lead_summary`
- `customer_needs`
- `discovery_questions`
- `follow_up_draft`
- `human_approval_required`

## Troubleshooting Highlights

### Required activity timestamp

HubSpot rejected the first note attempt because the activity timestamp was required. I mapped the current execution time to the note's activity date and verified successful creation.

### CRM associations

I mapped the HubSpot contact ID returned by the create/update action into both the note and task association fields. This ensured that each activity appeared on the intended contact timeline.

### Structured output mapping

I parsed the AI response into defined JSON fields before sending values to HubSpot. This made priority, score, reasoning, summary, needs, questions, and the follow-up draft individually addressable.

### Score consistency

One test exposed a mismatch where the component breakdown totalled seven but the returned total did not. I strengthened the output instructions, reran the scenario, and verified consistent totals across High, Medium, and Low tests.

### HubSpot note formatting

Raw newlines were collapsed or displayed as literal characters by HubSpot. I updated the AI formatting rule and note body to use HubSpot-compatible HTML breaks and non-breaking spaces, then verified a readable CRM note.

### Human-review task title

Dynamic text initially joined the priority and the word “lead.” I changed the title pattern to `[priority]-priority — Review AI follow-up — [full name]` and verified the final task in HubSpot.

## Cost Awareness

- Tally, Make, and HubSpot were used with free-tier functionality available during the build.
- OpenAI API usage is usage-based and may incur a small cost depending on model, prompt size, and volume.
- The prototype used GPT-5 nano during testing.
- No production-volume cost estimate or savings claim is presented.

