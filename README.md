# Agent security audits

Independent, reproducible checks of published AI-agent security claims. Each audit comes with scripts that anyone can re-run, and states what was and wasn't verified.

## What's here

| Audit | What it covers | Status |
|---|---|---|
| [Tenuo's "89 same-tool pairs" AgentDojo result](docs/audits/tenuo-agentdojo-89-same-tool-pairs.md) | Recomputed the headline (0 of 89 attacks scored) from the authors' raw logs. The number reproduces, but the benchmark's attack scorers have blind spots, and the arms that reach zero complete about half as many tasks. | Published for comment. One model, one run per pair. |
| [Tenuo's approval gates](scripts/review_tenuo_approvals/README.md) | 25 checks of how human-approval gates behave on `tenuo==0.3.5`. Found that issuer warrants dropped approval settings; the maintainers fixed it in 0.3.4. | Docs improvement open at [tenuo-ai/tenuo#1074](https://github.com/tenuo-ai/tenuo/pull/1074). |

Plain-language write-up of the first audit: [Reproducing a "0% attack success" result](docs/blog/reproducing-a-zero-percent-result.md).

## Where the work went

- Proposal for a pre-execution authorization hook: [ethz-spylab/agentdojo#184](https://github.com/ethz-spylab/agentdojo/issues/184)
- Approval-handling bug report, confirmed and fixed in Tenuo 0.3.4: [tenuo-ai/tenuo#1029](https://github.com/tenuo-ai/tenuo/issues/1029)

## Running the scripts

- `scripts/audit_tenuo_agentdojo/`: run with `python -I`, with paths as arguments. See section 4 of the report. Scripts 01 to 05 need the authors' published experiment data; script 06 needs `agentdojo` installed.
- `scripts/review_tenuo_approvals/`: `pip install "tenuo==0.3.5"`, then `python 07_approvals_docs_claims.py`. Exit code 1 if any check fails.

## How this was done

The analysis was done with Claude Code. I ran the scripts myself and checked the results against the sources, and I take responsibility for the content. Corrections are welcome: open an issue.

## Related

This work started from my thesis project, [agent-security-gate](https://github.com/giselleevita/agent-security-gate), and is kept separate from it.

## License

Apache-2.0, see [LICENSE](LICENSE).
