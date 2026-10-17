# bioshazard/skills

Personal agent skills, kept small and editable.

## Skills

- [`eigen-grill-me`](skills/eigen-grill-me/SKILL.md) — find and ask the question that resolves the most downstream decisions.
- [`script-first`](skills/script-first/SKILL.md) — encode operational changes in a parameterized script, rehearse it, then execute and verify production.

## Install

Install with [skills.sh](https://skills.sh):

```sh
npx skills@latest add bioshazard/skills
```

Or symlink an individual skill for local development:

```sh
ln -s "$PWD/skills/eigen-grill-me" ~/.agents/skills/eigen-grill-me
```

## Attribution

`eigen-grill-me` began as `batch-grill-me`, copied from
[`mattpocock/skills`](https://github.com/mattpocock/skills/tree/main/skills/in-progress/batch-grill-me)
and adapted using Shishir Mehrotra and Matt Hudson's
[`Eigenquestions: The Art of Framing Problems`](https://docs.superhuman.com/@shishir/eigenquestions-the-art-of-framing-problems).
The copied material remains available under the MIT License. See
[`THIRD_PARTY_NOTICES.md`](THIRD_PARTY_NOTICES.md).
