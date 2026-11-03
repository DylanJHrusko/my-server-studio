# Lesson 01 · Conversation evidence

AI-drafted task summary, not a transcript or grade. It may be public. Use actual
short quotes or labeled paraphrases, name any help supplied, and link actual
work. Leave missing contributions Pending. A learner can review, correct or
remove excerpts before publication; accuracy approval is not proof of learning.
Label role-play honestly rather than treating it as an actual learner response.

**Lesson:** STUDIO-001. **Available conversation context:** one Claude Code
desktop session (AI coach: Claude) on November 3, 2026, working from this laptop
clone. Earlier sessions built the server, Traefik and HTTPS; they are not
summarized here.

## Try

*Paraphrase of my screenshot:* on the classroom calculator I entered 6 + 7; the
browser result (JavaScript) and API result (FastAPI) both showed 13 with
"Results match".

## Prediction

Before the plan was explained: "I think that it goes through the network, then
it will reach the server ( digital ocean ) then it'll hit my page through the
reverse proxy, then it'll go back to the person requesting and load"

*Help received:* after my prediction, the coach compared it with the plan and
added the steps I had not named: DNS lookup, TLS at Traefik on 443, the Host
rule selecting the calculator container, and the private `hosting-web` network
to port 8000.

## Check interpretation

About the local browser test that divides 6 by 0 and expects "Cannot divide by
zero." with no false match (it passed):

1. "Shows the calculator is working and running locally"
2. "It does not show the original site and it running locally without touching
   the original server"

*Help received:* the coach then contrasted this local test with the launch's
public HTTPS checks and explained positive vs. negative cases.

## Browser observation

On https://calc.trifffling.com with 6 × 7: "No padlock, has a docker commit and
build date, and result matched means results were correct". After one follow-up
question: "browser and api both show 42 and matching, yes connection is secure"

*Help received:* the coach explained that current Chrome shows a site-settings
icon instead of a padlock and suggested clicking it to check the connection; it
also asked for the actual numbers.

## Keep decision

"keep result as is because it is showing that locally and on the deploy the
results are the same and it is correct"

## Review

I reviewed these excerpts and approved them as accurate on November 3, 2026, before the first commit. Approval confirms the record's accuracy, not learning.

## AI work and next step

AI ran setup, configure, plan, report and the prepared `check`; I ran `doctor`
and `launch` in my own terminal (sudo). Evidence: [SPEC.md](SPEC.md),
[studio/evidence.json](studio/evidence.json),
[issue #1](https://github.com/DylanJHrusko/my-server-studio/issues/1).
Next: open the PR, record its actual CI, merge and close the issue.
