

<img align="center" width="197" height="240" alt="Puli-AI-new" src="https://github.com/user-attachments/assets/b1e21d97-35b2-4364-b62d-62d7f663c900" />

# 🛡️ Puli Guardian MCP

<img align="right" width="350" height="600" 
  src="https://github.com/user-attachments/assets/e0d31d86-2d8a-41d3-a1ff-7a47abb87b3a">

![Puli-demo-edited2-ezgif com-crop]()

### _**AI agents write code fast. Puli validates it against what actually matters.**_

### Puli Reviewer
is a proactive **quality** and **stability** guardrail for your <br>
AI coding agents (Claude Code, Cursor, Antigravity, etc.). <br> 
It prevents production breakages by confronting proposed <br> 
code changes with a massive, real-time knowledge layer consisted <br> 
of real-time bugs, release notes, past incidents, edge cases, regulations and security breaches. <br>

**Stop production errors before they happen.** Puli acts as a <br> real-time bridge between your local development and global the real world. <br> It doesn't just check syntax — **it checks reality.**

[How do I install it?](#install)

<br clear="right">

## 🚀 How it Works
<img align="right" width="450" height="750" 
  src="https://github.com/user-attachments/assets/b20008e8-b2f3-494a-95bf-ad74344f6456">

Whenver your coding agent attempts to modify your codebase, <br>
Puli:

1.  **Analyzes the Context:**<br>
Queries the agent to understand the intent of<br>
the change.

2.  **Cross-References Failures:**<br>
Matches the code against it's live-updated data layer<br>
of real-world real-time production errors and business-flow<br>
disruptions.

4.  **Reality check:**<br>
Forces the agent to account for specific edge<br>
cases before the code is ever committed.<br><br>
<img align="left" width="146" height="188" 
  src="https://github.com/user-attachments/assets/0a73df13-60bb-453c-bd11-c8e929dd7a7d">

<br clear="all" />

---

<a id="install"></a>
## ⚙️ Installation & Setup

### 1. Install dependencies
Make sure that uvx is installed on your station

### 2. Configure the MCP Server
Add the following to your coding agent's configuration (e.g., `claude_desktop_config.json` or your IDE's MCP settings):

```json
{
  "mcpServers": {
    "puli-viewer": {
      "command": "uvx",
      "args": ["--from", "puli-mcp-server@latest", "puli-reviewer"],
      "env": {
        "BYO_OPENAI_API_KEY": "Optional* - <your-key-if-using-byok>",
        "BYO_GOOGLE_API_KEY": "Optional* - <your-key-if-using-byok>",
        "BYO_ANTHROPIC_API_KEY": "Optional* - <your-key-if-using-byok>"
      }
    }
  }
}
```

* Provide at lease one API key

### 2. Add Agent Rules

To ensure your agent utilizes the guardrail for every change, add our rules file to your project:

* **For Cursor:** Create a file at `.cursor/rules/puli-reviewer.mdc` and paste the content from [our rules template here](https://drive.google.com/file/d/10mXrsaERDonnUIefV4GQ1hEXhJbZboZ6/view?usp=sharing).
* **For Claude-code:** Create a file at `.claude/rules/puli-reviewer.md` and paste the content from [our rules template here](https://drive.google.com/file/d/10mXrsaERDonnUIefV4GQ1hEXhJbZboZ6/view?usp=sharing).

---

## 🛡️ Privacy & Security
**We prioritize your IP security**! Operations run locally on your station. no code is shared with our cloud.<br>
**Zero Retention.** We embedd the semantical meanning of your code change in our cloud. Nothing is ever logged or stored.<br>
We use vertex's LLM and embedding, You can provide your own GCP credentials (set GOOGLE_CLOUD_PROJECT, GOOGLE_CLOUD_LOCATION env vars for the MCP server)
in this case **everything** will run locally on your station apart from the data layer query using emebedded vectors <br>
