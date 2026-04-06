# SOGo — Mojibake UTF-8 fix for 5.12.7

This branch contains a focused fix for mojibake in SOGo mail handling.

## Problem

Some UTF-8 characters were displayed incorrectly in mail compose/preview processing, resulting in mojibake instead of correct characters such as `č`, `š`, and `ž`.

In practice, the issue appeared in the mail handling path where HTML fragments were converted or wrapped without explicitly preserving UTF-8 semantics.

## Scope

This branch contains only the UTF-8 / mojibake fix on top of upstream `SOGo-5.12.7`.

Included commits:

- `4b229469c` — `fix(mail): declare UTF-8 when converting HTML fragment to text`
- `09563a3d3` — `fix(mail): declare UTF-8 when wrapping HTML preview fragments`

## What this patch does

This patch set makes the mail create/preview path explicitly preserve UTF-8 when:

- converting HTML fragments to text
- wrapping HTML preview fragments

The goal is to prevent incorrect character rendering and keep UTF-8 content intact through these processing steps.

## What is not included

This branch does **not** include:

- AlmaLinux 10.1 local build fixes
- S/MIME detached signature handling changes
- other local maintenance or experimental patches

Those changes exist separately and are intentionally excluded here so that the mojibake fix stays clean, focused, and easy to review.

## Purpose

The purpose of this branch is to publish the mojibake UTF-8 fix as a small and reviewable patch set, clearly separated from other local work.

## Related refs

- Branch: `mojibake-mail-compose-preview-utf8-fix-5.12.7`
- Tag: `mojibake-utf8-fix`
