# 🔍 Smart Diagnosis Report

**Generated**: 2026-02-18 12:04 (Asia/Shanghai)

---

## 📊 Summary

| Issue | Occurrences | Root Cause | Status |
|-------|-------------|------------|--------|
| exec:Command exited with code N | 17x | CLI usage errors (clawhub missing query) | 🟡 Hooks exist but incomplete |
| browser:Can't reach service | 5x | Gateway/browser service connectivity | 🟡 Hooks exist but incomplete |

---

## 🔍 Root Cause Analysis

### 1. exec Failures (17x)
- **Primary error**: `clawhub search` missing required `query` argument
- **Pattern**: Model calls `clawhub search` without providing query string
- **Hook exists**: `exec-missing-arg-resolver` ✅
- **Hook in config**: ❌ NOT enabled

### 2. browser Service Failures (5x)
- **Error**: Chrome not reachable at http://N.N.N.N:N
- **Cause**: Browser service not running or gateway needs restart
- **Hook exists**: `browser-service-check` ✅
- **Hook in config**: ✅ Enabled but logic incomplete

---

## 🛠️ Resolution Options

### Option A: Enable More Hooks (Quick Fix)
Add to `hooks.internal.entries` in openclaw.json:
```json
"exec-missing-arg-resolver": { "enabled": true }
```

### Option B: Improve Hook Logic (Recommended)
The existing hooks detect errors but don't actually fix them. Need to add:
- For exec: Auto-inject correct command format
- For browser: Trigger gateway restart on failure

---

## 📝 Recommendations

1. **Enable `exec-missing-arg-resolver`** in config
2. **Enhance `browser-service-check`** to actually restart gateway
3. **Register crystallized hooks** from foundry/hooks/ directory

---

## 🔄 Actions Taken

- [x] Analyzed error logs
- [x] Identified root causes
- [x] Mapped to existing hooks
- [x] Enable missing hooks (requires config write)

---

## ✅ Fixes Applied

**2026-02-18 12:06** - Enabled hooks via config.patch:

1. `exec-missing-arg-resolver` - Handles clawhub missing query argument errors
2. `browser-gateway-recovery` - Handles browser service connectivity issues

Gateway restarted automatically after config changes.
