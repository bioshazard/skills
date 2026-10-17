---
name: script-first
description: Turn operational recovery, repair, migration, or maintenance into a parameterized, rehearsed script before applying it to production. Use when the user says script first, make the procedure deterministic, automate the runbook, or wants a consequential operational procedure made repeatable. Not for ordinary application implementation or one-off read-only inspection.
---

# Script First

Beat the path into a script before pointing it at production. The deliverable is
an executable procedure with evidence that it works, plus its verified outcome
when execution is authorized. A transcript of successful shell commands is not
the automation.

## Discover and bound the operation

- Inspect existing automation, runbooks, incident logs, versions, and live state
  read-only. Extend the existing entry point when practical.
- Identify the exact target, desired result, protected originals, dependencies,
  data-loss boundary, and conditions that must stop execution.
- Resolve uncertain tool behavior against authoritative documentation. Pin
  version-sensitive dependencies where compatibility matters.
- Separate facts the agent can discover from decisions requiring the user.
  Preserve existing authorization; this skill does not require approval again.

## Encode the path

Put the operational sequence in a repository-owned script before consequential
production mutation. Choose the smallest suitable language and dependencies.
Discovery commands may remain interactive. An already authorized urgent containment
step may precede scripting when delay would worsen the incident; record it and
incorporate it into the repeatable procedure afterward.

Make the script's interface carry the decisions an agent would otherwise invent:

- Explicit environment/context, resource identities, source and destination,
  versions, backup identifiers, and recovery target where applicable. Do not use
  a production default or silently select the newest backup.
- A read-only plan by default and an explicit execution switch. Show resolved
  targets, actions, invariants, and expected effects. Distinguish planning from
  validation that actually exercises the operation.
- Preconditions before mutation: bind to resource identity as well as its name;
  reject drift, incompatible versions, missing inputs, and unexpected ownership.
- Secret references or protected files; no credentials in arguments, reports,
  logs, or Git. Honor restrictions on reading secret material.
- Bounded waits and retries, observable phases, meaningful exit codes, and a
  durable report of nonsecret inputs, versions, progress, and verification.
- Safe reruns: recognize completed work, recheck its identity and health, and
  resume only from verified checkpoints. On ambiguous partial state, stop with
  a precise recovery action instead of repeating destructive steps.

Keep originals and evidence until replacement and required backups are verified.
Make cleanup explicit and ownership-checked; protect production resources and
aliases to the same underlying storage. Do not force past failed safety gates.
For rollback, state what can actually be reversed and when new writes make a
return to the old state unsafe.

## Rehearse the executable procedure

Use isolated copies, disposable resources, or a representative test environment.
Ensure rehearsal cannot receive production traffic, write to production storage,
or use production identities for unintended mutations. Read-only sources must be
enforced read-only, not merely described that way.

Exercise the same script and relevant runtime that production will use, with
different explicit inputs. Test the risks that matter: wrong target rejection,
failure partway through, safe resume, repeated completion, and preservation of
protected resources. Use focused offline tests for safety logic and real checks
for integration behavior; a mock or successful dry run cannot prove recovery.

Define success from the workload's needs. For data recovery this may require
integrity checks, logical restore, semantic checks, runtime compatibility, and
application authentication. Report the recovered boundary and remaining uncertainty.

When rehearsal fails, fix the script and rerun the affected validation. Do not
establish an undocumented parallel path of manual fixes. If an emergency manual
action was necessary, incorporate it and verify the resulting script before
claiming repeatability.

## Execute and close

- Once relevant checks pass and execution is authorized, use the validated script
  against the explicit production target. Do not re-create the commands ad hoc.
- Stop on failed invariants or an unrecognized outcome; retain evidence. Do not
  expand the operation or invent destructive fallbacks to make it finish.
- Verify production data and workload behavior, then required backups. A ready
  process alone does not establish recovery success.
- Retire temporary resources only after preservation gates pass. Recheck health
  and safe completed-run behavior without replaying the mutation.
- Reduce the runbook to prerequisites, script inputs, invocation, verification,
  resume/rollback limits, and cleanup. Record actual results separately; label
  incident-specific examples so they are not reused as future live defaults.
- Report the outcome, evidence, remaining limitations, and script/runbook paths.
  If production execution was not authorized, deliver the tested artifact and
  concrete plan; ask only for the missing decision or authorization.

Do not promise universal determinism: make decisions explicit, behavior repeatable,
and uncertainty visible. Production drift must cause revalidation, not blind replay.
