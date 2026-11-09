# slurm-gridlock

**[Open the Slurm Queue Traffic Report →](https://niznik-dev.github.io/slurm-gridlock/)**

Why is my job still pending? A single-page explainer that answers that question for Slurm users, using a highway-traffic
metaphor in place of scheduler jargon.

## How it works

1. **Run one command** on a cluster login node. The page gives you the command. It only reads scheduler information
   (`squeue`, `sprio`, `sshare`, `scontrol`, `sacctmgr`) and saves it to `queue-report.txt` in your home folder.
2. **Bring the file to your computer**, using Open OnDemand or `scp`.
3. **Open it on the page.** Everything is processed in your browser tab. There is no server, no tracking, and nothing
   is saved.

There's also a demo button if you just want to look around.

## What it shows

| Section | What you learn |
|---|---|
| **Your spot in the merge order** | Your fairshare score for each account you can submit under, and where it puts you among everyone on the cluster |
| **Your waiting jobs** | A verdict for each pending job: stuck behind higher priority, waiting for hardware, held, over a limit, or asking for more than the partition allows. Also each job's place in line and its priority breakdown. |
| **How the merge order is decided** | The Fair Tree ranking, level by level, with how far each group is over or under its share |
| **The whole highway at once** | Every group and user on the cluster, sorted by merge order |
| **What you can do about it** | Suggestions ranked by how much they can help, from switching accounts to waiting out decay |
| **Check the toll** | What a job would cost in usage, and how it would shift your group's standing |

A glossary maps every road term to the real Slurm term it stands for (lane → partition, toll → TRES billing,
trip type → QOS, and so on).

## Caveats

- It explains **priority, not start time**. A job at the front of the line can still wait for free hardware.
- It's a simplified picture built from what Slurm shows every user. Treat the numbers as close estimates, not an audit.
- Pools with private queues (at Princeton, ailab and pli) are left out, because their data isn't visible to everyone.

## Development

The whole app is `index.html`: plain HTML, CSS, and JavaScript, with no build step and no dependencies. Open it in a
browser to run it locally. It's served by GitHub Pages from `main`.

## Credits

Built by [Mattie](https://niznik-dev.github.io) and Claude. Traffic theme suggested by
[Colm](https://github.com/ColmTalbot).
