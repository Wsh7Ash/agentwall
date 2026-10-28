# Weekly ops runbook - 2026-W44
Queue items: 4   Programs: 2   Skills matched: 26 of 50   Plan steps: 24

Thin coverage (no matched skill in these phases): portfolio

## program

duplicate-policy-review  (match 2)
  Understand how a program treats duplicates, race conditions and partial findings before you hunt, because duplicate rules decide whether popular surfaces are worth your hours at all
   1. Locate the duplicate rule in the policy and platform page, quoting it verbatim in your notes.
   2. Determine whether first-submitted or first-confirmed wins, because the two reward entirely different working styles.
   3. Check what partial credit exists for unique variants, such as a different root cause reaching the same impact.
   4. Estimate crowd density from the program's public bounty count versus its scope size and popularity.
   5. Decide whether to race on popular surfaces or to pursue angles where fewer hunters can arrive first.
   6. Log the rule and your strategy choice together so later results can be attributed to the decision, not to luck alone.

reward-structure-analysis  (match 2)
  Decode how a program actually pays, from bounty tables and duplicate rules to hidden multipliers, so expected value is computed from published terms instead of hoped-for maximums
   1. Extract the full bounty table: severity bands, payout ranges, and which bands the program has actually paid historically.
   2. Identify multipliers and modifiers such as quality bonuses, first-reporter rules and duplicate handling.
   3. Model duplicate loss using the program's published duplicate rule and your own acceptance history, not optimism.
   4. Compute expected value per severity band as payout times acceptance probability minus duplicate discount.
   5. Compare programs on expected value per research hour, using effort estimates you recorded from past engagements.
   6. Revisit the model when the program edits its table, since reward structures change more often than scope does.

program-fit-scoring  (match 1)
  Score every candidate program against your real skills, access and payout expectations before spending a research hour, so limited capacity flows to programs you can actually win in
   1. List every program under consideration with its scope size, asset types, payout range and published response times.
   2. Score your own fit per program: matching expertise, tooling you already own, and whether the assets are reachable from your position.
   3. Weight payout against effort using your historical data, not the program's advertised maximum bounty.
   4. Record the score with one sentence of reasoning so a later review can challenge the judgment instead of re-deriving it.
   5. Rank programs and cut anything below your fit threshold, keeping the cut list with reasons rather than deleting it.
   6. Re-score whenever a program changes scope, payout bands or response commitments, because fit is a moving property.

## queue

dead-hypothesis-pruning  (match 1)
  Remove hypotheses whose assumptions no longer hold, with the falsification evidence recorded, so the queue reflects what is still testable rather than what was once plausible
   1. For each queue item, state the assumption it depends on and the evidence that would falsify that assumption.
   2. Test cheaply whether the assumption still holds, using a single request or a public changelog rather than a full session.
   3. Mark falsified items as dead immediately instead of letting them occupy ranked positions.
   4. Record what killed the item, with the observation, so future rounds do not resurrect the same idea.
   5. Re-check near-miss items whose assumption is weakened but not yet dead, and set a re-evaluation condition.
   6. Keep the queue pruned at each triage so dead weight never competes with live work for attention.

hypothesis-backlog-triage  (match 1)
  Run a recurring triage over your idea backlog so hypotheses are ranked, merged, split or killed on evidence rather than surviving indefinitely on the hope that they are promising
   1. Dump every backlog item with its creation date, current score and the last evidence attached to it.
   2. Merge items that describe the same underlying weakness from different angles, keeping the strongest framing.
   3. Split items that bundle several independent tests, because a compound item can neither be started nor finished.
   4. Kill items whose assumption has been falsified or whose target no longer exists, recording why each died.
   5. Re-score survivors against fresh information such as new scope, new tooling or newly observed behavior.
   6. Archive killed items instead of deleting them so future rounds do not resubmit the same dead idea.

signal-promotion-gating  (match 1)
  Promote a lead from observation to active queue item only when it clears declared evidence gates, so curiosity does not silently convert into committed research hours
   1. Define promotion gates in advance: in-scope confirmation, a testable hypothesis, an observable outcome and an effort band.
   2. Log every raw lead at observation time with the evidence that produced it, before judging its merits.
   3. Apply the gates mechanically at triage, promoting only leads that satisfy every gate on written evidence.
   4. Route ungated leads to a holding area with the specific missing gate named for each.
   5. Promote only as many leads as the week's capacity admits, ranking gated leads by expected value per hour.
   6. Audit promotions afterward to see which gates best predicted productive work, and tighten the ones that did not.

## reproduce

baseline-trigger-comparison  (match 2)
  Capture a correct-behavior baseline alongside the defective response so the difference is the evidence, eliminating arguments about what the system should have returned
   1. Capture the defective response in full, with request, status, headers and body.
   2. Construct the baseline: the same request under conditions where the product behaves correctly.
   3. Change only the one variable that distinguishes baseline from defect, so the diff isolates the cause.
   4. Capture the baseline identically and diff the two captures field by field.
   5. State which difference is the defect and which differences are expected noise.
   6. Attach both captures and the diff to the report so the claim can be audited without rerunning anything.

clean-room-reproduction  (match 2)
  Reproduce a finding from a fresh state with no residue from your own testing, so the observation is provably caused by the defect rather than by your setup
   1. Reset to a known baseline: new session, default settings, no leftover state from the earlier exploration.
   2. Perform only the documented steps in order, without improvising extra requests between them.
   3. Capture each request and response in sequence so the chain can be replayed and inspected by someone else.
   4. Confirm the defect appears with exactly the documented inputs and no hidden precondition you forgot to record.
   5. Repeat the sequence a second time from reset to confirm it is deterministic rather than incidental.
   6. Record any precondition that turned out to be required, since an undocumented precondition invalidates the repro.

cross-account-reproduction  (match 2)
  Prove a finding across distinct accounts and tenants so ownership and isolation claims rest on two independent identities rather than on one session's confused state
   1. Create two independent identities with no shared state, groups, teams or administrative links.
   2. Establish distinct owned data in each identity so ownership boundaries have something real to cross.
   3. Perform the triggering action as one identity and observe its effect on data owned by the other.
   4. Reverse the roles and repeat, confirming the boundary is consistently crossed rather than one-directional.
   5. Record identifiers for both sides of every crossing so the evidence shows exactly whose object moved.
   6. State in the report which direction worked, because asymmetric crossing often indicates a different root cause.

environment-matrix-reproduction  (match 2)
  Reproduce across a deliberate matrix of clients, accounts and configurations so the defect's blast radius is known before you describe it, not discovered during triage
   1. Define the matrix dimensions that could plausibly matter: browser, device, account role, plan tier and region.
   2. Select a minimal set of cells that separates the dimensions without exploding into full combinatorics.
   3. Run the reproduction procedure identically in each cell, changing only the dimension under test.
   4. Record a cell-by-cell result table with pass, fail or not-applicable for every combination tried.
   5. Identify the boundary: which dimension flips the behavior and which dimensions have no effect.
   6. Report the boundary as part of the finding, since the affected-surface claim depends on it.

flake-rate-measurement  (match 2)
  Measure how often a non-deterministic defect actually fires before reporting it, because an unquantified intermittent bug is the fastest way to lose triage credibility
   1. Define the trial: identical procedure, clean reset between attempts, fixed inputs and environment.
   2. Run a meaningful number of attempts, enough that the observed rate means something rather than one in three.
   3. Record every attempt with its outcome, timestamp and any variation you noticed, not only the successes.
   4. Compute the observed rate and a simple range so the claim is quantified instead of described as intermittent.
   5. Vary one suspected factor at a time to see which condition raises or lowers the rate.
   6. Report the rate, the trial size and the conditions, so triage knows exactly how hard reproduction will be.

minimal-repro-reduction  (match 2)
  Reduce a working reproduction to the smallest set of steps, fields and state that still triggers the defect, because triage trusts short repros and abandons long ones
   1. Start from the full working reproduction and identify each step, field and precondition it contains.
   2. Remove one element at a time, retesting after each removal, and keep the removal only if the defect still triggers.
   3. Record what each removed element actually contributed, since some elements affect severity rather than reproducibility.
   4. Repeat until no further removal keeps the defect alive, producing the minimal failing sequence.
   5. Verify the minimal version reproduces twice from clean state before adopting it as the canonical repro.
   6. Attach both versions when reporting: minimal for triage speed, full for context on how it was found.

prerequisite-chain-documentation  (match 2)
  Document every precondition a defect depends on, in order, so triage can rebuild your exact starting position instead of guessing at what state the test assumed
   1. List every precondition: account roles, feature flags, prior actions, data rows and entitlement states.
   2. Order the prerequisites so the chain can be executed top to bottom without improvisation.
   3. Mark which prerequisites are default, obtainable through the product, or requiring privileged access.
   4. State the time dependence: how long a precondition takes to establish and how long it remains true.
   5. Verify the chain by following it literally from a fresh environment and noting where the instructions were ambiguous.
   6. Attach the ordered chain to the report as its own section, separate from the trigger steps.

reproduction-consistency-reruns  (match 2)
  Re-run a finished reproduction on a separate day, session and vantage point to catch day-one luck before triage does it for you and files it as not-reproducible
   1. Set the finding aside for a defined interval so accumulated state and assumptions lose their grip.
   2. Re-run the full documented procedure from clean state, following only what is written, not what you remember.
   3. Note every point where the written procedure was ambiguous, then fix the procedure rather than your memory.
   4. Run the procedure from a second vantage point, different network or machine, to expose environment dependence.
   5. Compare outcomes across runs and record consistency explicitly in the report.
   6. If a run fails, treat the procedure as the suspect first and the defect as the second suspect.

## report

report-structure-authoring  (match 3)
  Lay out a report so a tired triage engineer gets summary, impact, reproduction and evidence in that order, without hunting through prose for the four facts they need
   1. Open with a two-sentence summary: what is wrong, on which asset, and what an attacker gains.
   2. Follow with impact stated in the product's terms: data exposed, action performed, or money affected.
   3. Place the reproduction as numbered steps with preconditions separated into their own short section.
   4. Attach evidence inline next to the claim it supports rather than collecting everything at the end.
   5. Close with severity rationale and any remediation direction you can justify from the evidence.
   6. Cut every sentence that does not serve comprehension, because length costs triage time and your credibility.

impact-quantification-framing  (match 2)
  Translate a technical observation into concrete business and user impact with numbers where honest numbers exist, because severity negotiations are won on impact, not on request cleverness
   1. State the primary harm concretely: what data, what action or what money is affected, and for whom.
   2. Quantify with observed facts: row counts visible, records per response, accounts affected by the boundary.
   3. Bound the claim honestly, naming what you did not test and what an attacker would still need.
   4. Distinguish demonstrated impact from plausible-but-untested impact and label each part of the report accordingly.
   5. Map the framed impact onto the program's severity scale with one line of reasoning per criterion.
   6. Keep a copy of the numbers you asserted so a later re-test can confirm they still hold after fixes.

evidence-attachment-curation  (match 1)
  Curate the minimum evidence set that proves each claim, redacted and ordered to match the report, so reviewers get confirmation without a wall of screenshots to decode
   1. List each claim in the report and name the one artifact that proves it, dropping everything that proves nothing.
   2. Order attachments to follow the report's section order so a reviewer can walk both in parallel.
   3. Redact secrets, tokens and third-party personal data while keeping enough structure to remain verifiable.
   4. Record what was redacted and why, so a missing field reads as deliberate rather than as a gap.
   5. Check that each attachment is legible at normal zoom, since an unreadable capture is not evidence.
   6. Verify no attachment contains a credential, internal hostname or path you would not publish.

reproduction-step-clarity  (match 1)
  Write reproduction steps that a stranger can execute verbatim, with exact values, exact order and no pronouns whose antecedent lives three lines above
   1. Replace every vague noun with the literal endpoint, field name, identifier or button label.
   2. Number the steps and make each one a single action with a single observable result.
   3. Move all assumptions about state into preconditions rather than leaving them implied between steps.
   4. Substitute real example values for ids, emails and tokens, using obviously fake but well-formed data.
   5. Read the steps as someone who has never seen the product and mark every place you had to guess.
   6. Have a second person follow the steps cold if any is available, and fix whatever they stumble on.

severity-justification-drafting  (match 1)
  Derive severity from the program's published criteria with an explicit written rationale per factor, so the number arrives argued rather than asserted and survives the first challenge
   1. Read the program's severity definitions verbatim and note the factors each band actually keys on.
   2. Score each factor separately from your evidence: attack vector, prerequisites, impact, scope and user interaction.
   3. State the reasoning for every factor, including factors you could not test and how you treated them.
   4. Compute the band from the factors rather than starting from a gut number and justifying backward.
   5. Pre-write the counterargument a skeptic would raise, and answer it inside the rationale.
   6. Keep the factor notes with the report so a post-fix re-rating can reuse the same reasoning structure.

## followup

bounty-amount-verification  (match 2)
  Verify the awarded bounty against the program's published table and your argued severity, so a misapplied band is caught within the payout window rather than accepted silently
   1. Pull the current published bounty table and note the band boundaries that applied at submission time.
   2. Confirm the severity that was actually assigned, which may differ from the severity you argued.
   3. Compute the expected amount from band and any modifiers such as quality bonuses or first-reporter rules.
   4. Compare expectation against the offer, checking band, currency and any platform fee deductions.
   5. Raise a discrepancy within the program's stated window with the table, band and calculation attached.
   6. Log the final amount and any correction so your reward model uses settled numbers rather than offers.

triage-response-handling  (match 2)
  Process a triage reply as a decision point rather than an email, classifying it into accept, clarify, duplicate or dispute with the next concrete action already named
   1. Read the reply fully before acting, since partial reads turn clarifications into premature defenses.
   2. Classify it into one of accept, clarify, duplicate, downgrade or reject, and record the classification.
   3. Identify the specific question or decision the reply contains, which is usually narrower than its tone.
   4. Prepare a response that answers only what was asked, with evidence attached rather than restated.
   5. Set the response deadline from the program's stated timeline and put it in your queue, not your memory.
   6. Log the outcome against the program so your health and payout models absorb the real signal.

unresolved-report-escalation  (match 2)
  Escalate a stalled report along a defined path with a written summary and evidence attached, so aging tickets get a decision instead of drifting past every published response window
   1. Confirm the report has actually exceeded the program's published window, citing the exact dates.
   2. Assemble a short escalation summary: what was submitted, when, what was asked, what was answered, what is owed.
   3. Route the escalation through the documented path first, such as the platform's escalation or tam contact.
   4. State a specific requested outcome, whether a decision, a severity discussion or a status confirmation.
   5. Escalate one level at a time, keeping each message factual and free of grievance.
   6. Log the escalation and its result so your program health model reflects how the program handles aging work.

disclosure-timing-coordination  (match 1)
  Coordinate any public disclosure with the program's stated timeline and fix state, so publishing informs users without blindsiding a team still shipping the patch
   1. Read the program's disclosure policy verbatim and record the conditions, delays and blackout periods it sets.
   2. Confirm the fix state with the program before publishing anything, rather than inferring from a changelog.
   3. Agree the date in writing if policy allows coordinated timing, and treat silence as not-yet-cleared.
   4. Draft the public write-up to omit details that would enable abuse of unpatched surfaces.
   5. Re-check the fix state on the publication date, since rollouts slip and dates silently stop being true.
   6. Archive the cleared date, the state confirmed and the published version with the finding record.

duplicate-claim-negotiation  (match 1)
  Respond to a duplicate verdict by testing whether it is truly the same root cause, and by arguing the narrower case where your finding proves something the original did not
   1. Obtain the original report's stated root cause and impact, or the platform's summary, before arguing anything.
   2. Compare root causes first, since shared symptoms with distinct causes are usually not true duplicates.
   3. Compare impact, asset and prerequisite differences item by item and write down which differences are real.
   4. If overlap is genuine, concede the duplicate plainly and ask what partial credit or acknowledgment applies.
   5. If overlap is partial, present the specific difference: different path, different prerequisite or different impact.
   6. Record the verdict and the program's duplicate rule interpretation for future expectations.
