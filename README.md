# AI Tools for Data Science

A curated, living reference of AI-powered tools available in the data science domain. This repo documents what each tool does, what it is capable of, and where it fits into a real-world data science workflow.

---

## Why This Repo Exists

The AI tooling landscape for data science is evolving fast. New tools launch frequently, existing ones expand their capabilities, and it is easy to lose track of what is available and what is worth using.

This repository exists to:

- Maintain a single, organized reference of AI tools relevant to data science
- Document the **capabilities** and **use cases** of each tool clearly
- Serve as a go-to resource when evaluating tools for a specific task
- Grow over time with examples, screenshots, and hands-on notebooks

---

## Repository Structure

Each AI tool gets its own dedicated folder at the root of this repository. There is no deeper nesting by category — every tool lives at the same level so it is easy to find and contribute to.

```
ai_tools_data_science/
├── README.md                  ← You are here — the master index
├── <tool-name>/
│   ├── README.md              ← Tool overview, capabilities, and use cases
│   ├── examples/              ← Code snippets, notebooks, scripts
│   └── screenshots/           ← UI screenshots, output samples, visuals
├── <tool-name>/
│   ├── README.md
│   ├── examples/
│   └── screenshots/
└── ...
```

---

## What Each Tool Folder Contains

Every tool folder follows the same structure:

### `README.md`
The primary document for the tool. It covers:

| Section | Description |
|---|---|
| **Overview** | What the tool is and who makes it |
| **Capabilities** | What the tool can do |
| **Use Cases** | Real-world scenarios where the tool is applied |
| **Pricing** | Free / Open-source / Paid / Freemium |
| **Links** | Official site, documentation, GitHub |

### `examples/`
Hands-on material — code snippets, Jupyter notebooks, or scripts that demonstrate how to use the tool.

### `screenshots/`
Visual references — UI screenshots, output samples, charts, or any visuals that help understand what the tool looks like in practice.

---

## Tools Index

| Tool | Category | Type |
|---|---|---|
| [Deepnote](./deepnote/) | Collaborative Notebooks | Freemium |
| [Hex](./hex_tech/) | AI Data Workspace | Freemium |

---

## Contributing

To add a new tool:

1. Create a folder named after the tool (lowercase, underscores for spaces) at the root
2. Add a `README.md` inside using the structure described above
3. Optionally add `examples/` and `screenshots/` folders
4. Add a row for the tool in the Tools Index table above

---

*Maintained by [ramprakash28](https://github.com/ramprakash28)*
