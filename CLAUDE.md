# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

Personal org-mode notes documenting the steps to set up a Linux desktop environment (Gnome, Emacs, tmux, Alacritty, fonts, etc.). There is no build, lint, or test tooling — the "execution" of these notes happens in Emacs via org-babel: code blocks are run with `C-c C-c` with point over them.

## Conventions

- Every new note file must be added to the *Sections* list in `README.org`.
- Blocks are `shell` or `emacs-lisp`. Prefer `emacs-lisp` blocks that use `url-copy-file`/`magit-clone` for downloads/clones over shell `wget`/`gh` scripting (an earlier pattern that was refactored away — see commits "download with emacs lisp", "remove dependency on Github CLI and shell scripting").
- Use org-babel features instead of shell glue: `:dir` for working directories (including TRAMP paths like `/sudo::` for root steps), `#+name:` plus `:var` to pass values between blocks, `:results` where output matters.
- Some blocks are intentionally non-executable documentation (e.g. `conf` blocks showing systemd override files, `#+begin_example` fragments). That is fine and expected.
- `.gitignore` covers Emacs lock/backup files (`*~`, `#*`).

## Machine-specific context

The notes target the author's machine: Debian-based, Wayland session, `emacs-pgtk` (Wayland build) on a HiDPI display. Where a distro file conflicts with a newer setup, notes prefer user-level overrides (e.g. a systemd drop-in over editing `/usr/lib/...`) and say so explicitly — preserve that style.

## Assets

`gtk-4/gtk.css` and `gtk-4/gtk-dark.css` are stylesheet files meant to be copied into `~/.config/` (referenced from `gnome.org`), not documentation.