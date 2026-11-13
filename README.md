# Design Extraction Skill

A portable Agent Skill for isolating or faithfully reconstructing visible artwork from mockups, signage, packaging, apparel, and souvenirs. It is not tied to Hermes or any one model. It requires an agent that can inspect images and create/verify files; the instructions alone do not supply image-editing tools.

## Use with different agents

- Claude Code: put this folder at `.claude/skills/design-extraction-skill/` in a project or `~/.claude/skills/design-extraction-skill/` for personal use. For claude.ai custom Skills, upload a ZIP of the skill folder where that feature is available.
- Gemini CLI: put this folder at `.gemini/skills/design-extraction-skill/` (or `.agents/skills/design-extraction-skill/`) in a project, or install/link it from a local directory using Gemini CLI's skill commands.
- ChatGPT: if Skills are available in your workspace, use Plugins > Skills > Create > Upload from your computer. Availability depends on your plan and workspace settings. Otherwise, provide `SKILL.md` in a conversation or Project and ask ChatGPT to follow it; that does not install a native skill.
- Other Agent Skills-compatible assistants: put the folder in their documented skills directory. In plain chat interfaces, provide the `SKILL.md` text as instructions; automatic discovery is not guaranteed.

Before submitting an image, the user must crop it to the exact subject/design to extract, leaving a small margin without cutting off any artwork. If the crop is missing, ambiguous, or cuts off essential details, the agent asks for a corrected crop and waits instead of choosing a target itself. The full original may be provided as additional context.

Give the agent the best-resolution crop. The generated artwork must be clean and high quality: remove accidental grain, compression speckles, stray pixels, and mask-edge noise while preserving sharp lettering, fine lines, and intentional texture. Denoising cannot restore missing detail. The default deliverables are two separate files: the isolated artwork PNG and `artwork_editable.svg` with native vector shapes/groups and live text where feasible, intended for editing in Adobe Illustrator. An SVG containing only an embedded bitmap is not considered editable; the agent must disclose raster-only or substituted elements rather than inventing detail. No extraction report or separate preview is produced.

Format: `design-extraction-skill/SKILL.md` with standard `name` and `description` frontmatter. The folder name and skill name match.

Maintainer: Razie93.
