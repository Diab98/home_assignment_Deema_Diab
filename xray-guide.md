---
title: The Translation & AI Persona Challenge
description: This article describes the Xray build blocker enhancement.
audience: Developer.
---

# Automatically block builds on critical vulnerabilities in Xray

The `yaml` configuration flag `block_on_critical_cve` enhances Xray scans by enabling automatic build blocking when critical vulnerabilities are detected. By enforcing a strict policy during scanning, it helps prevent vulnerable artifacts from progressing through the software delivery pipeline.

The feature is supported in Xray version 3.85 or later. Earlier versions do not recognize the configuration and will ignore it. When enabled, builds fail immediately if a vulnerability with a Common Vulnerability Scoring System (CVSS) of 9.0 or higher is found, returning an error code 500.

## Prerequisites

- Xray version 3.85 or later

- Authenticated JFrog CLI

## Parameters

`block_on_critical_cve`

`enfore_critical_block`

## Code sample

The following example demonstrates how to enable critical vulnerability enforcement in a `yaml` configuration. The configuration ensures that any detected critical vulnerability immediately stops the build process.

```yaml
xray:

  scanning:

    enforce_critical_block: true
```

## Settings file guidelines

The following configuration allows you to enforce strict security gates in your CI/CD pipelines. By enabling immediate failure on scans and blocking builds when critical vulnerabilities are detected, you can ensure that high-risk components never reach staging or production environments. You can implement this in security-sensitive workflows where compliance, risk reduction, and rapid feedback are essential. It is especially valuable in regulated environments or production pipelines where even a single critical CVE must halt delivery until resolved.

```yaml

scan_settings:

fail_on_scan: true

  block_on_critical_cve: true

   allow_grace_period: false
```

## AI Usage Notes

Before running Copilot, I outlined the structure of the user guide I wanted and edited the developer’s brief into a cohesive paragraph. Then, I asked Copilot to “Optimize the LLM prompt structure” to ensure it was refined for LLM consumption. I also asked it to refine the brief but I didn't quite like the output it returned, because Copilot embellished the information. So, the brief that appears at the end of my **Optimized prompt** is mostly my edit.

The initial output Copilot returned for my optimized prompt was decent, but:

- It added unnecessary prerequisites, such as a `yaml` environment (too basic of a prereq) and added that users require appropriate permissions to run scans (not included in brief).
- Added explanations under the **Parameter** section that I didn't request.
- Didn't list ‘block_on_critical_cve’ as a parameter.

After I was satisfied with the user guide, I asked Copilot to turn the output into Markdown format so that I may copy it into the `.md` file.

### Optimized prompt

Create a structured user guide for the Xray feature that automatically blocks software builds. The intended audience is developers.

**Requirements**

Follow this exact structure and formatting:

1. Heading

    - Provide a clear, descriptive title for the user guide.

1. Introduction

    - Write no more than two concise paragraphs.
    - Explain:
        - What the Xray feature does
        - Its purpose
        - Any key limitations or scope considerations

1. Prerequisites

    - List required conditions, configurations, or dependencies users must meet before using the feature.

1. Parameters

    - Provide a brief, clear description of the relevant configuration parameter(s).
    - Must explicitly include: `enforce_critical_block: true`

1. Code Sample Section

    - Begin with a short introductory sentence explaining what the sample demonstrates.
    - Include a properly formatted Markdown code block.
    - Ensure you use the parameter name `enforce_critical_block: true` in the configuration guide.

**Additional Guidelines**

- Keep the writing concise, technical, and user-focused.
- Use clear headings and consistent formatting.
- Avoid unnecessary explanations or verbose language.
- Spell out acronyms on first mention.
- Ensure the output is ready for documentation use without further editing.

**Feature brief**

The feature is an enhancement to Xray scans. It’s a YAML configuration flag called ‘block_on_critical_cve’ that is supported by Xray version 3.85 or later. This flag is not supported in earlier versions and will be ignored if used, so upgrading is required. Before using the configuration flag, users must authenticate the JFrog CLI. When ‘block_on_critical_cve’ is set to true: If a CVSS score of 9.0 or higher is detected, the build fails immediately and returns an error code 500.

---
