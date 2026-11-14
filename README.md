# incident-rca

A Claude plugin that turns raw incident evidence into a blameless postmortem.

After an outage, the on-call engineer is left with logs, alert history, and a messy chat thread. Writing the RCA takes hours and often gets skipped. This plugin does the first draft in minutes: it builds the timeline, separates trigger from root cause, runs the 5 whys, and writes action items someone can own.

## What you get

| Skill | What it does |
|---|---|
| `/incident-rca:rca` | Writes a full postmortem from logs, alerts, chat exports, or rough notes |
| `/incident-rca:timeline` | Builds an ordered incident timeline with detect, mitigate, and resolve times |
| `postmortem-format` | The structure and writing rules Claude follows for any postmortem |

Claude also uses these skills on its own when you ask for an RCA, a postmortem, or an incident timeline.

## Install

In Claude Code:

```
/plugin marketplace add ashishjsharda/incident-rca
/plugin install incident-rca@incident-rca
```

## Use

Point it at your evidence:

```
/incident-rca:rca ./logs/api-2026-11-10.log ./notes/incident-channel.txt
```

Or paste the evidence and ask:

```
/incident-rca:timeline
<paste alert history and chat messages>
```

The RCA is saved as `postmortem-<incident-name>.md` in your current directory.

## What the postmortem contains

- Summary and impact, with numbers
- Timeline in one timezone, each event tied to its source
- Trigger, root cause, and contributing factors, marked confirmed or suspected
- 5 whys that end at a process or design gap, never at a person
- What went well, what went poorly, where we got lucky
- Action items typed as prevent, detect, or mitigate, each with an owner role, priority, and a "done when" test
- Open questions the evidence does not answer

## Data and privacy

This plugin is instructions only. It has no MCP server, no hooks, no scripts, and makes no network calls. It reads only the files you point it at and sends nothing anywhere beyond your normal Claude session.

[Privacy](https://github.com/ashishjsharda/incident-rca/blob/main/PRIVACY.md)

## License

MIT
