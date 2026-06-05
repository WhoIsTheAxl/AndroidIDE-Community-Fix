# 🔧 The Fix: Bypass GPG Verification

You need to edit the AndroidIDE repository file and add `trusted=yes` — this tells `apt` to skip signature verification.

## Step-by-Step in Termux/AndroidIDE Terminal

### 1. Install a text editor (if you don't have one)

```bash
pkg install nano
```

2. Find the AndroidIDE repository file

```bash
ls $PREFIX/etc/apt/sources.list
```

You're looking for a file named sources.list

3. Edit the file

```bash
nano $PREFIX/etc/apt/sources.list
```

4. Change this line (what you probably have)

```
# The main AndroidIDE repository
deb https://packages.androidide.com/apt/termux-main/ stable main
```

5. To this (the fix)

```
deb [trusted=yes] https://packages.androidide.com/apt/termux-main stable main
```

6. Save and exit

Ctrl+X → Y → Enter

7. Update packages again

```bash
apt update
```

## ⚠️ Security Note

This fix disables GPG verification for the AndroidIDE repository.
Only use it if you understand the trade-off:
- ✅ Gets AndroidIDE working immediately
- ❌ Reduces package security (theoretical risk)

## 🔄 How to Revert (When Key Is Fixed)

```bash
# Restore original sources.list
cp $PREFIX/etc/apt/sources.list.bak $PREFIX/etc/apt/sources.list
apt update

✅ The error should be gone!
✅ Tested!