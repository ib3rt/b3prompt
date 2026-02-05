# 🤖 Always Build: Create Your Persistent AI Workflow

*Learn how to build an autonomous system that researches, learns, builds, and publishes while you sleep.*

---

## 🎯 What You'll Learn

By the end of this tutorial, you'll have:
- ✅ An autonomous workflow that runs when agents are idle
- ✅ A research pipeline that finds trending articles automatically
- ✅ A content production system that publishes to GitHub
- ✅ A complete learning loop that improves over time

**Time to complete:** 15-20 minutes  
**Level:** Intermediate  
**Prerequisites:** Basic command line, Git, cron

---

## 📖 Introduction

What if your AI system could:

> Research trending topics while you sleep, learn new techniques, build useful tools, create content, and publish everything automatically?

That's exactly what **Always Build** does.

In this tutorial, you'll create a persistent workflow system that:
1. **Monitors** agent activity
2. **Researches** 3 trending articles when idle
3. **Learns** from findings
4. **Builds** documentation and code
5. **Produces** blog posts and tutorials
6. **Publishes** to GitHub automatically

---

## 🏗️ Architecture Overview

```
┌─────────────────────────────────────────────────────────┐
│                   ALWAYS BUILD SYSTEM                    │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌──────────────┐    10-min check    ┌────────────────┐│
│  │  Heartbeat   │ ──────────────────▶│  Idle Check    ││
│  │  (Cron Job)  │                    │                ││
│  └──────────────┘                    └───────┬────────┘│
│                                              │         │
│                              ┌───────────────┴─────────┐│
│                              │                         ││
│                              ▼                         ▼│
│                     ┌──────────────┐         ┌──────────┐│
│                     │ Agents Busy? │ NO      │ Execute  ││
│                     │              │         │ Workflow ││
│                     └──────┬───────┘         └────┬─────┘│
│                            │                      │      │
│                     YES ◀──┴──▶ NO                ▼      │
│                              │           ┌──────────────┐│
│                              │           │  Research    ││
│                              │           │  Learn       ││
│                              │           │  Build       ││
│                              │           │  Produce     ││
│                              │           │  Publish     ││
│                              │           └──────────────┘│
│                              │                         │
│                              └─────────────────────────┘
│                                                          │
└─────────────────────────────────────────────────────────┘
```

---

## 📁 Directory Structure

Create this structure for your workflow:

```
memory/always-build/
├── research-YYYY-MM-DD.md   # Daily research findings
├── activity-log.md          # Session history
└── research-template.md     # Template for articles

tools/
└── always-build-trigger.sh  # Main trigger script
```

---

## 🔧 Step 1: Create the Trigger Script

Create `tools/always-build-trigger.sh`:

```bash
#!/bin/bash

# Always Build - Persistent Workflow Trigger
# Runs every 10 minutes via cron
# Executes only when ALL agents are idle

LOG_FILE="$HOME/.openclaw/logs/always-build.log"
ALWAYS_BUILD_DIR="$HOME/.openclaw/workspace/memory/always-build"
TIMESTAMP=$(date '+%Y-%m-%d %H:%M:%S')

log() {
    echo "[$TIMESTAMP] $1" >> "$LOG_FILE"
}

log "🔍 Checking agent status..."

# Check if any agents are active
ACTIVE_AGENTS=$(ps aux | grep -E "agent|openclaw" | grep -v grep | wc -l)

if [ "$ACTIVE_AGENTS" -gt 0 ]; then
    log "⏸️  Agents busy ($ACTIVE_AGENTS active) - Skipping workflow"
    exit 0
fi

log "✅ All agents idle - Starting Always Build workflow"

# Create today's research file
TODAY=$(date '+%Y-%m-%d')
RESEARCH_FILE="$ALWAYS_BUILD_DIR/research-$TODAY.md"

# Start workflow
cat > "$RESEARCH_FILE" << EOF
# Always Build - Research Session
**Date:** $TIMESTAMP

## 📚 Research in Progress...
- Searching for 3 trending articles...
EOF

log "📚 Research session started: $RESEARCH_FILE"
log "🎯 Ready to execute: Research → Learn → Build → Produce → Publish"
```

Make it executable:
```bash
chmod +x tools/always-build-trigger.sh
```

---

## 📝 Step 2: Create the Research Template

Create `memory/always-build/research-template.md`:

```markdown
# Always Build - Research Template

**Date:** {{DATE}}  
**Session:** {{SESSION_ID}}  
**Status:** {{IN_PROGRESS|COMPLETE}}

---

## 📚 Article 1: [TITLE]

**Source:** [URL]  
**Topic:** [Category]  
**Relevance:** [How it connects to your system]

### Key Insights
- Point 1
- Point 2
- Point 3

### Actionable Takeaways
- Action 1
- Action 2
- Action 3

### Implementation Opportunity
[Description]

---

## 📚 Article 2: [TITLE]

[Same structure...]

## 📚 Article 3: [TITLE]

[Same structure...]

---

## 🎯 Top Priority Actions

1. **Highest Impact:** [Action] - [Why]
2. **Quick Win:** [Action] - [Time]
3. **Long-term:** [Action] - [Outcome]

## 📝 Learning Notes

[Key learnings]

## 🚀 Next Steps

- [ ] Action 1
- [ ] Action 2
- [ ] Action 3

---

*Generated by Always Build Workflow*
```

---

## 📊 Step 3: Setup the Cron Job

Add to your crontab (`crontab -e`):

```bash
# Always Build - Runs every 10 minutes
*/10 * * * * cd ~/.openclaw/workspace && ./tools/always-build-trigger.sh >> ~/.openclaw/logs/always-build.log 2>&1
```

Verify it's running:
```bash
crontab -l | grep always-build
```

---

## 🔄 Step 4: The Complete Workflow

When triggered, the system executes these phases:

### Phase 1: Research (30% of effort)
```bash
# Research 3 trending articles on:
- AI agent development
- Automation & workflows  
- Web development trends
- Content marketing

# For each article:
- Summarize key insights
- Extract actionable takeaways
- Identify opportunities
```

### Phase 2: Learn (20% of effort)
```bash
# Process research findings
- Identify 1-2 new techniques to implement
- Document learning in memory/always-build/
- Update knowledge base
```

### Phase 3: Build (30% of effort)
```bash
# Create or improve:
- Documentation
- Templates
- Code snippets
- Workflow automation

# Focus areas:
- Agent enhancements
- Content pipeline improvements
- System documentation
```

### Phase 4: Produce (15% of effort)
```bash
# Generate content:
- Blog posts
- Tutorial guides
- Agent task definitions
- Process documentation
```

### Phase 5: Publish (5% of effort)
```bash
# Push to appropriate repositories
git add -A
git commit -m "Always Build: $(date '+%Y-%m-%d') research"
git push origin main

# Update documentation hub
# Announce to relevant agents
```

---

## 📈 Output Structure

Your system will generate:

```
memory/always-build/
├── research-2026-02-05.md    # Day 1 findings
├── research-2026-02-06.md    # Day 2 findings
├── research-2026-02-07.md    # Day 3 findings
├── activity-log.md           # All sessions
└── research-template.md      # Template
```

### Sample Research Output

```markdown
# Always Build - Research Session
**Date:** 2026-02-05 01:17

## 📚 Article 1: New AI Agent Patterns

**Source:** https://example.com/ai-agents  
**Topic:** AI Agent Development  
**Relevance:** Directly applicable to Life OS

### Key Insights
- Multi-agent coordination is becoming standard
- Voice interfaces are next frontier
- Autonomous coding agents improving rapidly

### Actionable Takeaways
- Implement agent-to-agent communication
- Add voice interface capability
- Enhance autonomous coding features

### Implementation Opportunity
Life OS could use multi-agent coordination for Super Swarm expansion.
```

---

## 🎯 Best Practices

### 1. Stay Focused
- Research only topics relevant to your system
- Prioritize actionable insights over theoretical

### 2. Document Everything
- Save all research
- Log all sessions
- Track improvements over time

### 3. Iterate
- Review activity log weekly
- Adjust focus areas based on results
- Refine the workflow

### 4. Automate Publishing
- Push to GitHub automatically
- Update docs on each build
- Announce to relevant agents

---

## 🔍 Troubleshooting

### Cron not running?
```bash
# Check cron status
sudo systemctl status cron

# Start cron
sudo systemctl start cron

# Check logs
grep CRON /var/log/syslog
```

### No research generated?
```bash
# Check trigger script
cat ~/.openclaw/logs/always-build.log

# Verify permissions
ls -la tools/always-build-trigger.sh
```

### Agents never idle?
```bash
# Check active processes
ps aux | grep agent

# Review agent activity
cat ~/.openclaw/logs/agents.log
```

---

## 📊 Metrics to Track

| Metric | Description | Target |
|--------|-------------|--------|
| Research Sessions | Articles researched per week | 30+ |
| Build Sessions | Code/docs created per week | 10+ |
| Content Published | Blog posts/tutorials per month | 5+ |
| Agent Idle Time | Hours system builds autonomously | 20+ |

---

## 🚀 Next Steps

After completing this tutorial:

1. **Run the first workflow manually:**
   ```bash
   cd ~/.openclaw/workspace
   ./tools/always-build-trigger.sh
   ```

2. **Check the output:**
   ```bash
   cat memory/always-build/research-$(date +%Y-%m-%d).md
   ```

3. **Review the logs:**
   ```bash
   cat ~/.openclaw/logs/always-build.log
   ```

4. **Adjust the workflow** based on your needs

---

## 🎉 Congratulations!

You've built an autonomous AI workflow system that:

✅ Runs every 10 minutes  
✅ Researches trending topics automatically  
✅ Builds documentation and code  
✅ Produces content  
✅ Publishes to GitHub  

**Your system is now ~Always Building~!** 🚀

---

## 📚 Related Lessons

- [Universal Vibe Coding Prompt](./universal-vibe-coding-lesson.html)
- [Agent Swarm Coordination](../agents/swarm-coordinator.html)
- [Content Pipeline Automation](../content-pipeline.html)

---

*Part of the b3prompt.com AI Prompt Improvement Course*
