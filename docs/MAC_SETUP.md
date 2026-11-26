# Mac setup — DONE 2026-11-26 (Rashids-MacBook-Pro)

Run once in Terminal on the Mac:

```
mkdir -p ~/dev && cd ~/dev && git clone https://github.com/rashidtung/project-registry.git
mkdir -p ~/.codex ~/.claude
sed 's#C:\\Users\\rashid\.iqbal\\project-registry#~/dev/project-registry#g' ~/dev/project-registry/docs/codex-global-AGENTS.md >> ~/.codex/AGENTS.md
sed 's#C:\\Users\\rashid\.iqbal\\project-registry#~/dev/project-registry#g' ~/dev/project-registry/docs/claude-global-CLAUDE.md >> ~/.claude/CLAUDE.md
(crontab -l 2>/dev/null | grep -v project-registry; echo '0 * * * * cd $HOME/dev/project-registry && /usr/bin/git pull --rebase --autostash -q && /usr/bin/git push -q') | crontab -
cd ~/dev/project-registry && git push
sed -i '' 's#project-registry\\skills#project-registry/skills#g' ~/.codex/AGENTS.md ~/.claude/CLAUDE.md
```

Check: `ls ~/dev/project-registry; tail -4 ~/.codex/AGENTS.md; crontab -l`

Then: in Claude and Codex on the Mac, re-link each project to its folder under `~/OneDrive`. Test: ask either tool for the next action on Tstop.

When done, change the title of this file to "Mac setup — DONE <date>".
