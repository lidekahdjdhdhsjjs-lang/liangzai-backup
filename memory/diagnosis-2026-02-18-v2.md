# 🔍 Smart Diagnosis Report - Update

**Generated**: 2026-02-18 18:05 (Asia/Shanghai)

---

## 📊 Current Status

| Issue | Count | Status |
|-------|-------|--------|
| exec:Command exited (code 1) | 203x | 🔴 Persistent |
| exec:Command exited (code 127) | 25x | 🔴 jq not found |
| exec:Command exited (code 255) | 18x | 🔴 Unknown |
| browser:Chrome not reachable | 27x | 🔴 Persistent |
| edit:Non-unique text | 5x | 🆕 New |
| message:Action requires target | 30x | 🔴 Persistent |

---

## 🔍 Root Cause Analysis

### 1. exec:Command exited (code 127)
- **Cause**: `jq` command not found on system
- **Solution**: Use Python/json parsing instead of jq, or install jq

### 2. exec:Command exited (code 1)
- **Cause**: Multiple issues:
  - `clawhub search` missing query argument
  - Various CLI errors
- **Hooks enabled**: exec-missing-arg-resolver ✅

### 3. browser:Chrome not reachable
- **Cause**: Browser service not running / gateway needs restart
- **Hooks enabled**: browser-gateway-recovery ✅

### 4. edit:Non-unique text (NEW)
- **Cause**: Using short/common text that appears multiple times
- **File**: discord-2026-02-15.md has duplicate content

---

## 🛠️ Recommended Fixes

### Fix 1: Create jq replacement hook
Instead of using `jq`, use Python or grep for JSON parsing.

### Fix 2: Improve edit tool hook
Add a hook that validates edit text uniqueness BEFORE calling edit.

### Fix 3: Pre-call validation hooks
Add `before_tool_call` hooks to validate parameters before execution.

---

## 📈 Tool Success Rate

From foundry metrics: 94%+ success rate overall

The recurring failures are edge cases that need better pre-validation.

---

## ✅ Fixes Applied (2026-02-18 18:07)

**New hooks created and enabled:**

1. `edit-unique-text-validator` - Handles edit non-unique text errors (5x)
2. `exec-jq-not-found` - Handles jq command not found (25x)

**Previously enabled hooks:**

1. `exec-missing-arg-resolver` - clawhub query errors
2. `browser-gateway-recovery` - browser service issues
3. `exec-exit-code-check` - general exit code errors
4. `browser-service-check` - browser service detection
5. `message-auto-target` - message target auto-detection

Gateway restarted to load new hooks.
