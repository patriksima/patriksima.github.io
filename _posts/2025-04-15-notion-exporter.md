---
layout: post
title: Export Notion Data Effortlessly from the Command Line
subtitle: .NET CLI open source tool
tags: [notion,tools,cli]
---

# Introducing NotionExporter: Export Notion Data Effortlessly from the Command Line

If you've ever needed to get structured data out of [Notion](https://notion.so) — for reporting, integration, backups or analysis — you know it's not as straightforward as it seems. That's exactly why I built **NotionExporter**: a simple yet powerful command-line tool that lets you export databases, pages, blocks, and more, directly from Notion's API into clean JSON files.

## 🚀 What is NotionExporter?

**NotionExporter** is a Windows command-line application written in C# and powered by .NET. It connects to the [Notion API](https://developers.notion.com/), authenticates using your integration token, and allows you to fetch and export data in a structured, scriptable, automatable way.

### Key Features:

- 🔄 Export entire databases, individual pages, or nested blocks
- ⚙️ Filter and sort data using Notion's query syntax (via JSON file)
- 🔐 Secure token handling via CLI, environment variables or prompt
- 💾 Output data to a file or stream it to stdout
- 🧰 Built on `Spectre.Console.Cli` for beautiful, structured CLI
- 🧪 Supports scripting and automation (PowerShell & CI/CD friendly)

---

## 🧪 Real-world Example: PowerShell Pipeline

Want to extract and list all names from a Notion database? Here's how:

```powershell
.\NotionExporter.exe export database --id <your-database-id> |
  ConvertFrom-Json |
  % { $_.results } |
  % { $_.properties.Name.title[0].plain_text }
```

Need to filter your database export to only include this week's entries? Just pass a query:

```powershell
.\NotionExporter.exe export database --id <your-id> --filter-file query.json
```

**query.json**:
```json
{
  "filter": {
    "property": "Date",
    "date": { "this_week": {} }
  }
}
```

---

## ⚙️ How It Works

Under the hood, NotionExporter uses:

- `HttpClientFactory` with typed clients for safe API requests
- Configuration via `appsettings.json`, environment or CLI
- Secure input for API token (with masking)
- JSON serialization with `System.Text.Json`
- Clean, testable architecture (handlers, services, interfaces)

---

## ⚙️ Prerequisites

1. Get your token from [Notion integrations](https://www.notion.so/my-integrations) and pass it via `--token` or set `NOTION_API_TOKEN` in your environment.

---

## 📥 Installation Options

You have two options to get started with **NotionExporter**:

---

### 🟢 Option 1: Download Prebuilt Release (Recommended)

1. Go to the [Releases page](https://github.com/patriksima/NotionExporter/releases)
2. Download the latest `.zip` for Windows:
    - `NotionExporter-win-x64.zip`
3. Extract the archive and run:

```powershell
.\NotionExporter.exe [command] [options]
```

✅ This version is self-contained — **you don't need to install .NET runtime**.

---

### 🔵 Option 2: Build It Yourself (Requires .NET SDK)

1. Install [.NET SDK 9.0 (preview)](https://dotnet.microsoft.com)
2. Clone the repository:

```bash
git clone https://github.com/patriksima/NotionExporter.git
cd NotionExporter
```

3. Build the app:

```bash
dotnet build -c Release
```

4. Or publish a self-contained version:

```bash
dotnet publish -c Release -r win-x64 --self-contained true -o publish
```

5. Then run:

```powershell
.\publish\NotionExporter.exe [command] [options]
```

---

## 🤝 Contributions Welcome

This is an early-stage tool and feedback, ideas, and pull requests are welcome. Whether it's a new feature, bug fix, or documentation improvement — I'm all ears.

You can also file issues, suggest features, or help test new functionality.

---

## 🔐 Security

Found a security issue? Please report it privately. See [SECURITY.md](https://github.com/patriksima/NotionExporter/blob/master/SECURITY.md) for details.

---

## 📄 License

MIT licensed — use it, extend it, and make it yours.

---

Stay tuned for future improvements, including support for `search`, `comments`, and smarter data exports!
