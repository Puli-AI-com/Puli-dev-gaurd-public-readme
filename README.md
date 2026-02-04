# Puli Reviewer MCP

**Puli Reviewer** is a proactive security and stability guardrail for your AI coding agents (Claude Code, Cursor, Antigravity, etc.). It prevents production breakages by confronting proposed code changes with a massive, real-time database of global incidents, edge cases, and security breaches. 

<table>
  <tr>
    <td width="50%" valign="top">
      <h3>🚀 How it Works</h3>
      <p>
When your coding agent attempts to modify your codebase, Puli Reviewer:

1.  **Analyzes the Context:**

Queries the agent to understand the intent of the change.

2.  **Cross-References Failures:**

Matches the code against a live-updated DB of real-world production errors and business-flow disruptions.

3.  **Stress Tests:**

Forces the agent to account for specific edge cases before the code is ever committed.
      </p>
      <ul>
        <li>Real-time incident database</li>
        <li>Privacy-focused architecture</li>
        <li>Seamless agent integration</li>
      </ul>
    </td>
    <td width="50%" valign="top">
      <video src="https://github.com/user-attachments/assets/f10afac2-c57c-4b52-8d7d-8fc78946e00f" 
             controls="controls" 
             style="max-width: 100%;">
      </video>
    </td>
  </tr>
</table>

---

## ⚙️ Installation & Setup

### 1. Configure the MCP Server
Add the following to your coding agent's configuration (e.g., `claude_desktop_config.json` or your IDE's MCP settings):

```json
{
  "mcpServers": {
    "puli-viewer": {
      "command": "uvx",
      "args": ["--from", "puli-plg@latest", "puli-reviewer"],
      "env": {
        "BYO_OPENAI_API_KEY": "<your-key-if-using-byok>"
      }
    }
  }
}
```

### 2. Add Agent Rules

To ensure your agent utilizes the guardrail for every change, add our rules file to your project:

* **For Cursor:** Create a file at `.cursor/rules/puli-reviewer.md` and paste the content from [our rules template here](https://drive.google.com/file/d/1e2qbVHWiT6zAE2VYYVbXrydT8iRz1HlH/view?usp=sharing).
* **For other agents:** Ensure the agent is instructed to:
    > "Consult Puli Reviewer before finalizing any file edits."

---

## 🛡️ Privacy & Security
We prioritize your IP security with two distinct working modes:

| Mode | How it Works | Data Privacy |
| :--- | :--- | :--- |
| **Bring Your Own Key** | Uses your own OpenAI/Anthropic API key. | **Local Only.** No code is shared with our cloud; only DB patterns are fetched. |
| **Internal Key** | Uses Puli's managed API keys. | **Zero Retention.** Code passes through our infra for processing but is never logged or stored. |
