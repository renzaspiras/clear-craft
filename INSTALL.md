# Install Clear Craft

Clear Craft includes four skills: **Clear Progress**, **Evidence-Driven Engineering**, **Interface Craft**, and **KI Control**. The plugin has no MCP server or connected app to authorize.

## Codex CLI or Codex desktop from GitHub

The GitHub repository is private, so make sure Git can access it as `renzaspiras` before adding the marketplace.

1. Add the repository as a Codex plugin marketplace:

   ```sh
   codex plugin marketplace add renzaspiras/clear-craft
   ```

2. In Codex desktop, restart the app if needed. Open the Plugins Directory, choose **Clear Craft**, and install the plugin.

3. To enable the marketplace plugin in a trusted Codex project, add this to that project's `.codex/config.toml`:

   ```toml
   [plugins."clear-craft@clear-craft"]
   enabled = true
   ```

4. Start a new Codex session and confirm all four skills appear in the plugin.

To check or refresh the marketplace later:

```sh
codex plugin marketplace list
codex plugin marketplace upgrade clear-craft
```

The marketplace catalog is at `.agents/plugins/marketplace.json`; it points to the plugin at the repository root.

## ChatGPT account plugin

The creator has already created Clear Craft as a private personal plugin. In the same ChatGPT account, open **Plugins → Personal → Created by you**, select **Clear Craft**, then install it. This private account plugin is separate from the GitHub source repository.

## Install the skills directly

For an agent host that discovers standalone skills, copy the three skill folders into a project's `.agents/skills/` directory:

```sh
gh repo clone renzaspiras/clear-craft
mkdir -p .agents/skills
cp -R clear-craft/skills/clear-progress clear-craft/skills/evidence-driven-engineering clear-craft/skills/interface-craft clear-craft/skills/ki-control .agents/skills/
```

Start a new agent session so it discovers the installed skills. For user-wide Codex discovery, use `~/.agents/skills/` instead of the project's `.agents/skills/`.

## References

- [OpenAI: Package and install plugins](https://developers.openai.com/plugins/build/plugins)
- [OpenAI Help: Plugins in ChatGPT](https://help.openai.com/en/articles/20001256-plugins-in-chatgpt)
- [OpenAI: Skill installation paths](https://developers.openai.com/api/reference/cli)
