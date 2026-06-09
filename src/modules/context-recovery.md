# Module 7 — Context Recovery

## Purpose

Allow users to resume work instantly after interruptions, eliminating the time and frustration lost to re-orienting after a context switch.

## The Problem

ADHD users are frequently interrupted — by calls, notifications, environment, or their own thoughts. Each interruption can cost 15–30 minutes of re-orientation. Over a day, this adds up to hours of lost productivity.

## Example Recovery Screen

```
Welcome Back.

Last completed:
  Arena Resorts homepage.

Next action:
  Create room pricing section.

Estimated completion:
  12 minutes.

[Resume]  [Change task]
```

## How It Works

1. When the user returns after an absence, the system detects the gap
2. It retrieves the last active task and progress state from the session log
3. It presents a clean, focused summary — no scrolling, no searching
4. One tap resumes the session

## Design Rationale

Context recovery removes the most painful part of ADHD interruption: the blank-screen paralysis of "where was I?" The system carries the memory so the user doesn't have to.
