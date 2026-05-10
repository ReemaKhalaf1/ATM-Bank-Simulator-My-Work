# 🏦 FIN Bank ATM Simulator — My Individual Contribution

**Role:** Project Manager & Core Developer  
**Team Project:** [ATM-Bank-Simulator-2.0](https://github.com/lellacf26658-dev/ATM-Bank-Simulator-2.0)  
**My GitHub:** [ReemaKhalaf1](https://github.com/ReemaKhalaf1)

---

## ✅ Features I Fully Implemented

### 1. Dynamic Account Creation (Create Account)
- Users can register a new account directly at the ATM with no hardcoded data.
- **What I did:** Added `STATE_CREATE_ACC` to UIModel (4‑step flow), wrote `createAccount()` in Bank, and linked it to a "NEW" button in View.
- **File changes:** `UIModel.java`, `Bank.java`, `View.java`, `Controller.java`

### 2. 5‑Minute Temporary Account Lock + Last Attempt Warning
- After **3 failed logins**, account locks for exactly **5 minutes** (auto‑unlocks — fairer than a permanent lock).
- On the **second failure**, user sees: *"Warning: 1 attempt remaining before your account is locked for 5 minutes."*
- **What I did:** Timestamped lock using `HashMap<String, LocalDateTime>`, warning message in the login branch.
- **File changes:** `Bank.java` (login method), `UIModel.java` (STATE_PASSWORD branch)

### 3. AuditLogger.java (Full Class Created by Me)
- Writes **every** login attempt, transaction, error, and lock event to `audit.log` with a timestamp.
- Directly meets **FCA audit trail** requirements.
- **What I did:** Created the whole file from scratch, integrated it into Bank.login(), createAccount(), etc.

### 4. DataManager.java + Auto‑Save (Full Class Created by Me)
- Serialises the whole `Bank` object to `bank_data.ser` after **every** transaction.
- On restart, the saved state loads automatically so balances survive a restart.
- **What I did:** Wrote the class, added `autoSave()` calls after deposit/withdraw/transfer/createAccount.

### 5. Large Transaction Confirmation (Withdrawals over £500)
- When user withdraws >£500, system asks for a **second ENT press** before executing.
- Prevents accidental or coerced high‑value cash outs.
- **What I did:** Added confirmation flag in `UIModel.processWithdraw()`.

### 6. Mini Statement with Masked Account Number (GDPR compliant)
- Displays **last 5 transactions** with the account number shown as `****` (only last 4 digits visible).
- Built on the `Transaction` class.
- **What I did:** Created `getMiniStatement()` in `BankAccount`, masked account number, added `processMiniStmt()` in UIModel and "STMT" button in Controller/View.

### 7. Last Login Time (Security Feature)
- Balance screen shows the **date and time** of the user’s most recent successful login.
- Helps detect unauthorised access.
- **What I did:** Added `lastLoginTime` field to `BankAccount`, updated it inside `Bank.login()`, displayed it in `UIModel.processBalance()`.

---

## 📂 Files I Created (from scratch)

| File | Purpose |
|------|---------|
| `AuditLogger.java` | Writes every security‑sensitive action to `audit.log` with a timestamp. |
| `DataManager.java` | Handles serialising/deserialising the whole bank data to disk. |

---

## 📝 Files I Modified (Key contributions)

| File | What I added/changed |
|------|----------------------|
| `Bank.java` | `createAccount()`, timed‑lock logic, `autoSave()`, `getLoggedInAccount()`, `getNumAccounts()` |
| `BankAccount.java` | `lastLoginTime`, `getMiniStatement()` (masked account number), transaction recording |
| `UIModel.java` | `STATE_CREATE_ACC`, `processMiniStmt()`, large transaction confirmation, last‑attempt warning |
| `Controller.java` | New actions: `"NewAcc"`, `"Stmt"` |
| `View.java` | Added "NEW" button, `setKeyboardInputEnabled()` for password entry |

---

## 🧪 Testing & Accountability

- **Manual testing:** Verified every feature (Create Account → login → lock → Mini Statement → Auto‑Save → audit.log)
- **GitHub commits:** All my changes are under my GitHub account (`ReemaKhalaf1`) in the team repository.
- **Audit log sample:** 
---

## 🔗 Links

- **Team repository:** [ATM-Bank-Simulator-2.0](https://github.com/lellacf26658-dev/ATM-Bank-Simulator-2.0)
- **My own archive (this repo):** [ATM-Bank-Simulator-My-Work](https://github.com/ReemaKhalaf1/ATM-Bank-Simulator-My-Work)

---

> *This document summarises my individual work on the FIN Bank ATM Simulator project for module CI453. I acted as both **Project Manager** (sprint planning, coordination, merging) and **Core Developer** (security, audit, data persistence, account creation, Mini Statement).*
