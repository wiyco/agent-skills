# agent-skills

A repository for managing "skills" for LLM agents such as Claude Code, Gemini CLI, and Codex CLI.

## Overview

This repository maintains a collection of custom instructions and tool definitions designed to extend the capabilities of LLM agents. These skills enable agents to autonomously perform complex tasks, including browser automation and specialized development workflows.

## Project Structure

- `.claude/skills/`: Skill definitions tailored for Claude Code.
- `.gemini/skills/`: Skill definitions tailored for Gemini CLI.
- `.agents/skills/`: Skill definitions tailored for Codex CLI.

## Available Skills

### 1. playwright-cli

Fast and headless automation of browser interactions (clicking, typing, screenshots, network mocking, etc.) using [microsoft/playwright-cli](https://github.com/microsoft/playwright-cli). Ideal for QA (Quality Assurance) automation, E2E testing, and data extraction from web pages.

### 2. ship-it

Automates the end-to-end development workflow, including branch creation, committing, opening Pull Requests, and requesting reviews. It supports and enforces Conventional Commits.

## Usage

Each agent automatically loads the shared skill definitions from `.claude/skills/` via symbolic links within the repository.

- **Claude Code**: Directly loads from `.claude/skills/`.
- **Gemini CLI**: Uses `.gemini/skills/`, which is a symbolic link to `../.claude/skills/`.
- **Codex CLI**: Uses `.agents/skills/`, which is a symbolic link to `../.claude/skills/`.

No additional setup is required if you are using these agents within this workspace. For use in other projects, you can create a symbolic link from this repository's skill directories to your project's agent configuration folder.

## Guidelines for Agents

- `AGENTS.md` (and its symbolic links `CLAUDE.md`, `GEMINI.md`): A standardized template containing general instructions for agents. This template can be copied into other repositories to provide consistent guidance and workflow definitions for LLM agents.
